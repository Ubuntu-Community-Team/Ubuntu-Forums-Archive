---
title: "Installing a small icon thingy in the right hand corner?"
date: 2012-02-20
forum: General Help
---

### Post by bbno3 on 2012-02-20
[http://www.omgubuntu.co.uk/2012/02/easily-monitor-system-resources-in-ubuntu-with-indicator-multiload/](http://www.omgubuntu.co.uk/2012/02/easily-monitor-system-resources-in-ubuntu-with-indicator-multiload/)

I want to install this but when i follow the terminal(as in drag and paste) i get 2 404 Errors on the last line, iv never been able to install anything like this without having problems, anyone have any ideas? >:

I'm using UBuntu 11.10

Heres the Error code

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by hwttdz on 2012-02-20
You ran these two lines:
```
sudo add-apt-repository ppa:indicator-multiload/stable-daily 
sudo apt-get update && sudo apt-get install indicator-multiload
```

And got said errors? I just installed the repo and had no issue reaching it.

---

### Post by bbno3 on 2012-02-21
I still get the same errors... i dont understand :confused:

---

### Post by stinkeye on 2012-02-21
The error is unrelated.
There is no xbmc release for oneiric in that ppa so it is returning an error.
```
[COLOR="Blue"]http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/[/COLOR][COLOR="Red"]oneiric[/COLOR]/main/binary-amd64/Packages
```

If you go to that ppa in the browser you get a **404 Not Found** page.

eg in the browser goto
```
[COLOR="Blue"]http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/[/COLOR]
```
and you will see there is no oneiric folder.


Whereas if you change it to maverick
```
http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/[COLOR="Red"]maverick[/COLOR]/main/binary-amd64/Packages
```
You get a package details page.

Have you or did you try to install xbmc?

---

### Post by bbno3 on 2012-02-22
No such file or directory.:(

---

### Post by stinkeye on 2012-02-22
Open software sources and unmark that ppa.

---

### Post by bbno3 on 2012-02-24
How? :confused:

---

### Post by grahammechanical on 2012-02-24
I also saw that page in OmgUbuntu and I was able to install indicator -multiload without any problems.

I do notice one thing. The code to install indicatior-multiload is:

> sudo add-apt-repository ppa:indicator-multiload/stable-daily 
sudo apt-get update && sudo apt-get install indicator-multiload

But the error messages that you have posted show that you are trying to install a completely different program - XMBC.

If you open Update Manager you will see a button marked Settings. click on that button and go to the Other Software tab. There you will see a list of those ppa that have been put as Software Sources. You can uncheck then or remove them by clicking the Remove button.

Regards.

---

### Post by stinkeye on 2012-02-24
> **bbno3 said:**
> How? :confused:

Hit the Super (Windows) key start typing in software sources amd
when it becomes the first one in the Applications list hit enter.
Under the **Other Software** tab look for the xbmc ppa you added.
Could be 2 entries...one for deb packages and one for source code.
Unmark or remove them.

---

