---
title: "Firefox help. pls"
date: 2009-08-09
forum: General Help
---

### Post by lb4406 on 2009-08-09
Should be a quick and easy solution (I hope) I just can't find the right phrase to search on to find the answer myself.

Using 9.04 I ran Firefox as SUDO from the terminal window 

(If anyone wants to know why it was just because I wanted to run the check for updates as it's 3.0.13 and thought it would be easier to install than manually doing it from the firefox website)

Ever since then Firefox only loads with a standard profile, i.e. none of my bookmarks etc appear.

If I run it again using SUDO from the terminal window then all my bookmarks and everything else appear as normal (except for the skin)

How to I reset it back to how it was?

Thanks:popcorn:

---

### Post by Barafu Albino Cheetah on 2009-08-09
```
sudo chown -R username ~/.mozilla
```
And avoid starting GUI apps as root.

---

### Post by lb4406 on 2009-08-09
Ahh that worked a treat,  its back to normal now, thanks a lot Cheetah!

---

### Post by lovinglinux on 2009-08-09
For future reference...

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by michy99 on 2009-08-09
> **Barafu Albino Cheetah said:**
> ```
sudo chown -R username ~/.mozilla
```
And avoid starting GUI apps as root.

Running GUI apps as root is useful sometimes, but it should be done with gksudo, not sudo:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

