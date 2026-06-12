---
title: "tail -f command (9.10)"
date: 2010-01-18
forum: General Help
---

### Post by OskarEi on 2010-01-18
Hello,

I hope I'm putting this in the right category.

tail -f <filename> is not working as planned on my Ubuntu 9.10, it doesn't show the appended data.

tail -F works, but it does not append the new line, it reopens the file with the message: "tail: <filename> has been replaced;  following end of new file"

I really hope I'm being silly, but I've used tail -f elsewhere without problems.

Any clues?
Thanks
Oskar

---

### Post by junapp on 2010-01-18
it should work exactly as you expect.

maybe try
```
tail --follow filename
```

but there should be no reason that works and -f does not that I can think of.

---

### Post by Leppie on 2010-01-18
which file are trying to monitor?
on my system it's working perfectly fine.
try the following command, while still active do some stuff and see if it appends:
```
tail -f /var/log/messages
```

---

### Post by OskarEi on 2010-01-18
Thanks for the reply guys, really appreciate it.

--follow does not work either.

I was having problems debugging my shell script so I decided to test it on a tempfile having two terminal windows open with the tail -f command on one side and editing the file on the other. No luck there.

tailing the /var/logs/messages works, but I'm not understanding why that works but not my testing-scenario nor in my shell script.

---

### Post by Leppie on 2010-01-18
> **OskarEi said:**
> Thanks for the reply guys, really appreciate it.

--follow does not work either.

I was having problems debugging my shell script so I decided to test it on a tempfile having two terminal windows open with the tail -f command on one side and editing the file on the other. No luck there.

tailing the /var/logs/messages works, but I'm not understanding why that works but not my testing-scenario nor in my shell script.
maybe your script doesn't do anything to trigger a message to be sent to the system or it's own log file?

---

### Post by fatihp on 2012-11-16
For future visitors like me, I have figured out that if you edit file with an editor(gedit etc.) "tail -f" command sees it as a new file, and doesn't show lines added...

On the other hand, if you append text lines to that file with a python script like this it works as expected:
```

with open("log-like.txt", "a") as myfile:
    myfile.write("\n appended text")

```

---

### Post by wildmanne39 on 2012-11-16
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

