---
title: "firefox installation problem???"
date: 2009-07-05
forum: General Help
---

### Post by kuldeepsidhu on 2009-07-05
i have deleted my firefox link from /usr/bin/ directory

i also deleted the firefox folder that exists in /usr/lib/

now when i want to make firefox from source it gives error..

but when i copy and the folder in the /usr/lib directory and i paste a link to the /usr/bin directory..but when i click on the link nothing happens...


there is no icon(shortcut)of firefox in the task bar...

how can i get all these settings back..?

do i need to restore my system..?i have not installed any backup software..how to resotre from log files plz tell me???

plz give link to firefox and the procedure how to install??

---

### Post by ibutho on 2009-07-05
You shouldn't have deleted Firefox in the way that you did. The right way would have been to use the package manager to uninstall it. What you could have done is leave the systems Firefox intact, install your version of Firefox into /opt (so your firefox directory would be /opt/firefox) and then change your preferred apps to use /opt/firefox/firefox as your default browser. Another option would be to use upgrade your systems Firefox using the method described [here]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html").

---

### Post by lovinglinux on 2009-07-05
Go to Synaptic and mark Firefox 3 for reinstallation. Then click apply. I think this should fix the problem.

For compiling Firefox 3.5  follow my guide "Compiling Firefox" from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by scouser73 on 2009-07-05
> **lovinglinux said:**
> Go to Synaptic and mark Firefox 3 for reinstallation. Then click apply. I think this should fix the problem.

For compiling Firefox 3.5  follow my guide "Compiling Firefox" from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Can I suggest that you view this site for installing Firefox 3.5: [http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

Many posts I've read regarding Firefox 3.5 lead to installing shiretoko, but that version isn't FF 3.5.  I installed FF 3.5 by using the link I am suggesting.

---

### Post by lovinglinux on 2009-07-05
> **scouser73 said:**
> Can I suggest that you view this site for installing Firefox 3.5: [http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

Many posts I've read regarding Firefox 3.5 lead to installing shiretoko, but that version isn't FF 3.5.  I installed FF 3.5 by using the link I am suggesting.

Thanks for your suggestion, but there are already enough methods to cause a lot of confusion. I received a post today making all sorts of complaints, because the user mixed instructions from different sections of the tutorial and missed important notes. So adding another method that does less than the ones available will just make it harder. Besides, this method s a single command, but then you have to manually add the links and run Firefox from home directory and edit other stuff, which make it more complicated.

Nevertheless, I have edited my instructions to make them more clear. If you want Firefox brand and not Shiretoko, follow the method **[COLOR="Sienna"]1 - Manual installation of fresh final releases from Mozilla[/COLOR]**. I have moved other methods that do not install the branded version to the end of that section and included more warnings, notes and red bold letters ;)

---

### Post by kuldeepsidhu on 2009-07-05
thanks

---

