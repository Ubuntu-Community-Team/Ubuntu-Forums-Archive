---
title: "HELP! Noob Screwed up"
date: 2010-03-03
forum: General Help
---

### Post by treacle80 on 2010-03-03
Hello,

I am a noob with linux.  In a fit of madness I managed to delete /usr/share/ folder.  Have i completely cocked up or can I recover the situation?

Right now I cant log-in to the gnome screen but can still log in through the recovery module.  However as a newbie i am not particularly comfortable with the command line...

PLEASE(!!!) can anyone help?

Cheers

---

### Post by darolu on 2010-03-03
You can try booting with the LiveCD and copying all the /usr/share folder to your hard drive, it _may_ work.

---

### Post by Primefalcon on 2010-03-03
Ouch I'm not exactly sure to be honest, thats.... a mess... you could try creating the folder manualy by

```
sudo mkdir /usr/share/
```

and then run 

```
sudo apt-get -f
```


If the above doesn't work you could try

and this is risky and [COLOR="Red"]**I'm not not sure if it'll even work or make things worse**[/COLOR].... but if you your system isn't usable....

```
sudo apt-get reinstall *
```

---

### Post by Primefalcon on 2010-03-03
before you try the dangerous thing above you could also try


```
dpkg --get-selections | xargs sudo apt-get reinstall
```

basicaly that just gets a list of everything installed and then reinstalls said list so should, recreate the /usr/share stuff

---

### Post by treacle80 on 2010-03-03
> **Primefalcon said:**
> before you try the dangerous thing above you could also try


```
dpkg --get-selections | xargs sudo apt-get reinstall
```basicaly that just gets a list of everything installed and then reinstalls said list so should, recreate the /usr/share stuff

Thanks for this - i ddon'twish to come across as completely stupid (!) ...but...

is that all one command and if so where is that vertical line(!) after selections...sorry to be so dense!  As i said i am a new boy

cheers

---

### Post by Primefalcon on 2010-03-03
dpkg --get-selections 
gets a list of all your installed packages installed



| is a pipe what it does it takes the output of one command and feeds it into another as input


xargs tells it to do each individually in this case for each package


sudo is a prefix that says do this with admin privileges


apt-get reinstall is what it appears to be, saying reinstall this package

---

### Post by Primefalcon on 2010-03-03
as for where the key is

hold down shift and press this key

[IMG]http://i50.tinypic.com/i5rlvo.jpg[/IMG]

---

### Post by mosshorn on 2010-03-03
If it is a fairly fresh install, use a liveCD to get what you need off of it, and reinstall. New installs (unless you have tons of stuff on there) save you a lot of frustration.

---

### Post by treacle80 on 2010-03-03
> **Primefalcon said:**
> dpkg --get-selections 
gets a list of all your installed packages installed



| is a pipe what it does it takes the output of one command and feeds it into another as input


xargs tells it to do each individually in this case for each package


sudo is a prefix that says do this with admin privileges


apt-get reinstall is what it appears to be, saying reinstall this package


Hey thanks for this - like to learn!

ok - typed as described and i get a return of

E: Invalid operation reinstall

any ideas?

I did have a lot on there so I am reluctant to lose everything...

---

### Post by Primefalcon on 2010-03-03
and sorry

```
dpkg --get-selections | xargs sudo apt-get --reinstall
```

---

### Post by treacle80 on 2010-03-03
Hey thanks for all your help...if I could buy you a pint I would!

Unfortunately the command hasn'tworked.  I think there are some critical python scripts in the share folder that have been deleted.  This will not allow the reinstallation of any files.

Nevermind - will know next time!...you have to screw up once in a while in order to learn!

Thanks for your help

---

### Post by Primefalcon on 2010-03-03
> **treacle80 said:**
> Hey thanks for all your help...if I could buy you a pint I would!

Unfortunately the command hasn'tworked.  I think there are some critical python scripts in the share folder that have been deleted.  This will not allow the reinstallation of any files.

Nevermind - will know next time!...you have to screw up once in a while in order to learn!

Thanks for your help
just a shame it never works.....

and thx for the pint

[IMG]http://t0.gstatic.com/images?q=tbn:Fu28Y0QREgn9lM:http://images.huffingtonpost.com/2009-07-30-beer.jpg[/IMG]

---

