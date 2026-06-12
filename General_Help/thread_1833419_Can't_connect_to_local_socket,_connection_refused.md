---
title: "Can't connect to local socket, connection refused"
date: 2011-08-26
forum: General Help
---

### Post by MattPhillips on 2011-08-26
I've been at this for a few days now and just can't crack the problem.  I have a local socket in /tmp/mysockets which I create successfully in a php script--

```
if (($sock = socket_create(AF_UNIX, SOCK_STREAM,0)) === false) 
{
    echo "socket_create() failed: reason: " . socket_strerror(socket_last_error()) . "\n";
        exit();
}
```

but to which I cannot connect, via

```
if (socket_connect($sock, $sock_str) === false) 
{
        echo "socket_connect() on " . $sock_str . " failed: reason: " . socket_strerror(socket_last_$
        socket_close($sock);
        exit();
}
```

This gives me 

> Warning: socket_connect(): unable to connect [111]: Connection refused in /var/www/myscript.php on line 66 socket_connect() on /tmp/mysockets/sock failed: reason: Connection refused

Now, obviously this sounds like a permissions issue, but I've chmod 777'ed the /tmp, mysockets, and sock, and it doesn't matter.  What could be the problem?

Matt

---

