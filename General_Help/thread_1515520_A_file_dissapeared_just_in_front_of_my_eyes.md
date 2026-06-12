---
title: "A file dissapeared just in front of my eyes"
date: 2010-06-22
forum: General Help
---

### Post by mrquesito on 2010-06-22
Hi, this is my first message in this forum. Yesterday I was playing around with Arduino, a programmable electronic device, and wrote a code that I saved (something of what I'm sure 100%) in the folder I usually save this kind of files.

Today I started the Arduino program, and clicked on "Recent Files" to open the file I was working with yesterday, but I wasn't there. I manually looked for it in the folder, but it was also gone from there. Suddenly, it appeared in the screen, and one second later it dissapeared again; it is quite weird :mad:. I've looked for some information, but I haven't found anything. I'd thank any information :)

---

### Post by potat on 2010-06-22
Do you remember what you called the file? If so, try in the terminal...
```

$ updatedb
$ locate foo.bar

```
where foo.bar is the name of your file.

---

### Post by sf-it-services on 2010-06-22
perhaps you should learn about things before you press execute...... where stuff goes is important, its why we use linux

---

