---
title: "having Problem with Firefox 7 after update"
date: 2011-11-13
forum: General Help
---

### Post by snakehorse on 2011-11-13
Hi,

I am getting below prompt in a terminal window while i open firefox:

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

This is coming after I ran update manager. When I close the terminal window, firefox shuts down too.

Please help me out.

Regards.

---

### Post by hansdown on 2011-11-13
Hi, snakehorse.

Were you running compiz, preveously?

Found some bug reports.

[http://www.google.com/search?client=ubuntu&channel=fs&q=WARNING%3A+Application+calling+GLX+1.3+function+%22glXDestroyPixmap%22+when+GLX+1.3+is+not+supported%21+This+is+an+application+bug%21&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=WARNING%3A+Application+calling+GLX+1.3+function+%22glXDestroyPixmap%22+when+GLX+1.3+is+not+supported%21+This+is+an+application+bug%21&ie=utf-8&oe=utf-8)

---

### Post by snakehorse on 2011-11-13
Hi,

I had actually put in command for firefox as "application in terminal" in shortcut. I just had to change it to "application" and it works fine. It might have been some compatibility issue, which i dont find worthwhile to explore unless it restricts my normal browsing.

Thanks for the reply.

---

### Post by raja.genupula on 2011-11-13
> **snakehorse said:**
> Hi,

I am getting below prompt in a terminal window while i open firefox:

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

This is coming after I ran update manager. When I close the terminal window, firefox shuts down too.

Please help me out.

Regards.

do frequent updates to your system  , its gonna solve the issue.
[http://ubuntuforums.org/archive/index.php/t-1693740.html](http://ubuntuforums.org/archive/index.php/t-1693740.html)

---

### Post by lovinglinux on 2011-11-13
I am not sure about the warning, but I think is a theme related issue. However, I don't think is something to worry about. It is just a warning.

About Firefox closing when when you close the terminal, that is normal with any application executed from terminal. If you don't want such behavior, start Firefox with this command:

```
firefox &
```

---

### Post by snakehorse on 2011-11-13
Thanks raja, lovinglinux.

---

### Post by vasa1 on 2011-11-13
> **lovinglinux said:**
> ...
About Firefox closing when when you close the terminal, that is normal with any application executed from terminal. If you don't want such behavior, start Firefox with this command:
```
firefox &
```
I'm just curious to know but why does one run Firefox from a terminal? Are there any situations in which this is more convenient?

---

### Post by lovinglinux on 2011-11-13
> **vasa1 said:**
> I'm just curious to know but why does one run Firefox from a terminal? Are there any situations in which this is more convenient?

What I can think of is to troubleshoot or if you need to run custom commands before or after Firefox.

---

### Post by vasa1 on 2011-11-13
> **lovinglinux said:**
> What I can think of is to troubleshoot or if you need to run custom commands before or after Firefox.

Okay, thanks for clearing that up!

---

