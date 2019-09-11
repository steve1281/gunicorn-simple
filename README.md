# gunicorn-simple
Learning gunicorn
# simple example of gunicorn

## create project
```
mkdir gunicorn-simple
cd gunicorn-simple/
python3 -m pip install --user virtualenv
python3 -m venv venv
source venv/bin/activate
pip install gunicorn
```

## create simple app (checked in)
```
cat myapp.py
def app(environ, start_response):
    data = b"Hello, World!\n"
    start_response("200 OK", [
        ("Content-Type", "text/plain"),
        ("Content-Length", str(len(data)))
    ])
    return iter([data])
```

## run simple app
```
gunicorn -w 4 myapp:app
```

## test simple app
```
[~]  $ curl localhost:8000
Hello, World!
```
