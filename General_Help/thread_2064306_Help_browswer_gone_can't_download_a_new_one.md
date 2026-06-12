---
title: "Help browswer gone can't download a new one"
date: 2012-09-28
forum: General Help
---

### Post by kristina4192 on 2012-09-28
I was having issues getting online, so I uninstalled google chrome, now I can't install a browser at all. It says my internet connection isn't there, but I can log on skype. Any suggestions?
Thanks

---

### Post by zombifier25 on 2012-09-28
What did you do in order to install a new browser? Because I believe the only thing you need to do is get on Software Center, or apt-get to install it.

---

### Post by Bashing-om on 2012-09-28
Kristina; Hi ! Welcome to the forum.

  You can do firefox per this link:
[http://www.cyberciti.biz/faq/install-firefox-13-0-tar-bz2-in-linux/](http://www.cyberciti.biz/faq/install-firefox-13-0-tar-bz2-in-linux/)

This is all from the command line..will take some time and thought..looks doable.

Be advised the current FF version is 15.0.1
[INDENT]kind regards <== BDQ

[/INDENT]

---

### Post by UltimateCat on 2012-09-28
What kind of issues were you having with your browser?
You may of just needed an add on or an update-

You can try Mozilla Firefox.
[http://www.mozilla.org/en-US/](http://www.mozilla.org/en-US/)

This is for updates for Firefox
[http://www.mozilla.org/en-US/firefox/update/](http://www.mozilla.org/en-US/firefox/update/)

You should be able to use the web browser that originally came with your distro.
Have you tried updating it?
For example when I want to update my web browser I open the terminal and run:
```
apt-get install -t squeeze-backports iceweasel

```
Of course your command will be different because your distro is Ubuntu 
So yours will look something like <#apt-get -t ubuntu (distro#)-backports mozilla firefox>

Some folks like Google Chrome or the web browser Chromium.

Hope this helps

---

### Post by kristina4192 on 2012-09-28
Hey guys thanks,
the problem is it's showing I don't have internet connection to download from the software center, and making me unable to follow that link. Like I said I know I have internet because I can log into skype. 
Thanks
kristina

---

### Post by Bashing-om on 2012-09-28
Kristina:

 You may have other problem => Package manager ?

Let's test that the package management works; what is the output of terminal command:
```
sudo apt-get update
```[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by kristina4192 on 2012-09-28
I dont really know how to use ubuntu well so i'm not sure what you mean by check terminal command, i'm sorry. I went into applications, accessories, and put that code in, is that what you meant? it put a whole list back with security.ubuntu.com....etc. please let me know if you mean something else.
I appreciate the help!

---

### Post by kristina4192 on 2012-09-28
hey i got it guys thanks! I did a complete update somehow (i've been trying for three days and it finally decided to work:) ) anyways it let me download firefox with it, thanks for all the suggestions!
much appreciated
kristina

---

### Post by UltimateCat on 2012-09-29
Hold down Ctrl + Alt + T
That should open the terminal and the background will be all black.
You'll se something like this:
```
kristina@linux$

```

Right after that $ sign type in 
sudo apt-get update

And copy and paste the results for us to read to help you.

---

### Post by Bashing-om on 2012-09-29
Outstanding ! // You do good work //

It is my desire that you be overjoyed with ubuntu. At any time you have questions or concerns, feel free to ask. We (being many) are here !
please mark this thread as solved (thread tools at top of post)... and carry on.

[INDENT]regards <==BDQ

[/INDENT]

---

