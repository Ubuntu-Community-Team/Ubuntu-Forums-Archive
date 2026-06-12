---
title: "Shell script background process management"
date: 2009-11-02
forum: General Help
---

### Post by hammad1337 on 2009-11-02
I have made a shell script which calls curl to download a file at some point:
```

curl --silent -x 192.168.162.248:81 --range xxxxxxx-yyyyyyy -o file.x http://www.server.com/file.zip &

```
I want to know if there is a way by which I can check when this curl process ends, so that if file downloaded has a size less than expected, I can re-invoke the command.
My script runs multiple instances of curl at the same time, so I'd like to differentiate between which one has ended, and to start that same command again.

---

### Post by geirha on 2009-11-02
You can wait for a background process (or all background processes) to complete with the builtin wait command.

You can also use the builtin kill command to poll whether a command is still running, by using signal 0.

```

$ sleep 5 &
[1] 31713
$ kill -0 %1 >/dev/null 2>&1 && echo "running" || echo "not running"
running
$ kill -0 %1 >/dev/null 2>&1 && echo "running" || echo "not running"
not running
[1]+  Done                    sleep 5
$ 

```

See [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement) for a more thorough explanation.

---

