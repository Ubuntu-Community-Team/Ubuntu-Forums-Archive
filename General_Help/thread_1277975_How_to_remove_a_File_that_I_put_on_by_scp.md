---
title: "How to remove a File that I put on by scp?"
date: 2009-09-29
forum: General Help
---

### Post by RuB3N on 2009-09-29
Hello, I was not sure which category this would be in so i just did general...

But anyways, I added a File to a server using scp its been a while but i do believe thats how. I need to know how to remove it from the server. I can use scp [email]your_username@remotehost.edu:foobar.txt[/email] /some/local/directory to copy it to my computer but its still on the actual server. If anyone knows a command that will do this I would greatly appreciate it!

---

### Post by brian mcgee on 2009-09-29
I would just SSH into that server and remove it. For example:
```
ssh username@server
```Then:
```
rm path/to/file
```

---

### Post by RuB3N on 2009-09-29
ok thank you and one last question how would I find the path to it?

---

### Post by RuB3N on 2009-09-29
i figured it out! think you for all the help!

---

