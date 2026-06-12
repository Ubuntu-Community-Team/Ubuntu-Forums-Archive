---
title: "port 8080 says cherrypy cannot open"
date: 2009-10-08
forum: General Help
---

### Post by superpink99 on 2009-10-08
OBJECTIVE:try to run this simple code
```
import cherrypy

class HelloWorld:
    def index(self):
        return "Hello World"
    index.exposed = True
    
cherrypy.quickstart(HelloWorld())

```

PROBLEM:
1. when i run it i get an error saying "**HTTP Port 8080 not free on 'localhost'**"
2. when i go to [http://localhost:8080/](http://localhost:8080/), it gives me this "503 service unavailable, cherrypy engine could not start.

Please help me..........

---

