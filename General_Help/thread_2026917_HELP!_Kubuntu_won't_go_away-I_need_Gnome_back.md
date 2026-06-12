---
title: "HELP! Kubuntu won't go away-I need Gnome back"
date: 2012-07-16
forum: General Help
---

### Post by sofasurfer on 2012-07-16
I screwed around when I was having desktop functionality problems. I installed KDE which gave me a Kubuntu login menu screen. I hate it. I am sorry for what I did and I ask for the wise ones to please help me get back to my old disfunctional life with Gnome and no login screen. I went to synaptic and reinstall gnome desktop manager and I did a complete removal of KDE desktop. I still have Kubuntu login. Please help me. I keep trying differant things and I know it is just a matter of time before I break it bad.

---

### Post by idoitprone on 2012-07-16
> **sofasurfer said:**
> I screwed around when I was having desktop functionality problems. I installed KDE which gave me a Kubuntu login menu screen. I hate it. I am sorry for what I did and I ask for the wise ones to please help me get back to my old disfunctional life with Gnome and no login screen. I went to synaptic and reinstall gnome desktop manager and I did a complete removal of KDE desktop. I still have Kubuntu login. Please help me. I keep trying differant things and I know it is just a matter of time before I break it bad.

```
sudo dpkg-reconfigure gdm
```
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by sofasurfer on 2012-07-16
Thank you Mr Wizard. That was so simple but I would never have found it.
However, I still get the kubuntu splash screen. Its ok if I am stuck with it because at least the login prompt is gone. Do I need to live with it or is there a fix? Is the splash screen simple a graphics choice? I think I saw an option to change the graphic in ubuntu tweek.

---

### Post by claracc on 2012-07-16
Following link : [http://askubuntu.com/questions/122242/how-do-i-remove-kubuntu-full-and-all-its-applications](http://askubuntu.com/questions/122242/how-do-i-remove-kubuntu-full-and-all-its-applications) give you some sugestions.

I hope it can help.

---

### Post by sofasurfer on 2012-07-16
I followed the above link and it was all so confusing. But I found a link on that page that sent me to  [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)
I simply copyed and pasted their command and it worked. It was really scary cause as the terminal was running it looked like my whole file system was being deleted. But when it was dome gnome desktop is working again. I did have to reinstall kaffeine and I may have to reinstall a couple other things but it is no big deal.
I had forgot about psycocats. It is a great website.
Thanks

---

### Post by claracc on 2012-07-16
You are welcome.

Glad you have solved your problem.

Please mark the thread as solved with "thread tools" in the upper right part of the page.

---

