---
title: "Skype as Startup Application"
date: 2012-09-28
forum: General Help
---

### Post by rbscairns on 2012-09-28
I have Skype 4.0.0.9 installed. I would like Skype to open on startup.

What I tried was Applications>System Tools>Preferences>Startup Application and then added Skype with Name = Skype and Command = Skype. Upon restarting and logging in, Skype does not automatically start.

How can I get Skype to open on startup?

---

### Post by HiImTye on 2012-09-28
make sure in 'Command:' it is a lower case 'skype' and not 'Skype'

---

### Post by Speransky on 2012-09-28
Sometimes Skype needs to be run at startup with little delay, like this:
```
sh -c "sleep 20 && skype"
```

---

### Post by rbscairns on 2012-09-28
It was an upper case problem. Now that the command is all lower case, it works fine.

Thank you.

---

