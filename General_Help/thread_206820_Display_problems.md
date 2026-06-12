---
title: "Display problems"
date: 2006-06-30
forum: General Help
---

### Post by lreyes6 on 2006-06-30
Hi there... 

I'm having problems displaying some applications on Xubuntu, the applications are OpenOffice.org 2.0 and Zsnes 1.4.. 
the problem is that  the border of the windows looks really bad... here is the image of the window from both programs... 

[ATTACH]11998[/ATTACH]
[ATTACH]11999[/ATTACH]

any idea how to solve this??

btw im running ubuntu on a IBM Thinkpad 600X (PIII 500Mhz, 128Ram)

thanks for the help :grin:

---

### Post by atoponce on 2006-06-30
[quote=lreyes6]Hi there... 

I'm having problems displaying some applications on Xubuntu, the applications are OpenOffice.org 2.0 and Zsnes 1.4.. 
the problem is that  the border of the windows looks really bad... here is the image of the window from both programs... 

[ATTACH]11998[/ATTACH]
[ATTACH]11999[/ATTACH]

any idea how to solve this??

btw im running ubuntu on a IBM Thinkpad 600X (PIII 500Mhz, 128Ram)

thanks for the help :grin:[/quote]

Your RAM is most likely causing the problem.  I would upgrade to a minimum of 256MB before running X.  Also, run in the terminal

```
sudo dpkg-reconfigure xserver-xorg
```

and change your driver to 'vesa' and see what happens.

---

