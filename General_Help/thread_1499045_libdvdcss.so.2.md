---
title: "libdvdcss.so.2?"
date: 2010-06-01
forum: General Help
---

### Post by Lyerae on 2010-06-01
Well, I figured out how to copy dvds, but it's saying I need "libdvdcss.so.2", which I can't find anywhere....
Help?

---

### Post by dino99 on 2010-06-01
you need to add "medibuntu" to the sources.list (synaptic repo)


[http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by Lyerae on 2010-06-01
I followed the steps and added this: 

> deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src  [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free

but when I ran "sudo apt-get update", I got this:
> W: GPG error: [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)


---

### Post by ajgreeny on 2010-06-01
You should have used the one long command which is easiest copied from the medibuntu website.

Here it is anyway.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```This is a single long string of text, not separate lines as it seems to be on that site.

Copy it and paste into terminal after removing the lines you already added, or you will end up with duplicates which apt-get does not like very much.

---

### Post by Lyerae on 2010-06-01
Aha! It works! Thanks for the help guys! :D

---

### Post by darolu on 2010-06-01
It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.

---

### Post by loungedaddy on 2010-06-19
This was a huge help for me too. Thanks. Esp to darolu

---

### Post by Foxcow on 2010-06-19
> **ajgreeny said:**
> You should have used the one long command which is easiest copied from the medibuntu website.

Here it is anyway.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```This is a single long string of text, not separate lines as it seems to be on that site.

Copy it and paste into terminal after removing the lines you already added, or you will end up with duplicates which apt-get does not like very much.

Thank you sir!  That is exactly the line I was trying to find.

---

### Post by gorsebush on 2010-07-19
And a great big thanks from me too.  I tried Darolu's suggestion and it appears to have worked perfectly.  Thanks to ajgreeny and foxcow as well for taking an interest.

---

### Post by theonlyalterego on 2010-08-12
Not sure if it was overkill but I ran both of the following, and everything is now working as expected. Thanks!

> **ajgreeny said:**
> You should have used the one long command which is easiest copied from the medibuntu website.

Here it is anyway.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```



> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.

---

### Post by WTBCompPro on 2010-08-31
> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.


Thanks that did it for some reason mediubuntu didn't work.

---

### Post by Chrispy764 on 2010-09-10
> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.


Yep, thanks, that worked for me and now I can view my older Disney DVD's. Does anyone know if this works on current releases? I am fairly new to Ubuntu and haven't bought or rented a DVD in years so I was curious if it works on new releases.

Thanks again.

---

### Post by blackhawkover on 2010-10-06
Thanks so much. 
I had to update and reboot, but it worked great then. 
Thanks.

---

### Post by cj13579 on 2010-11-09
> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.

Thank you very much for this. Just what I needed!

---

### Post by dbain25 on 2010-11-21
So, after installing these two solutions, do I need to do a restart? :-k

---

### Post by smannem on 2010-11-27
You helped me very much. thanks...

---

### Post by checoimg on 2011-02-15
> **dbain25 said:**
> So, after installing these two solutions, do I need to do a restart? :-k

I just Loged out and loged in and it works fine already making an Iso image

---

### Post by jeffreylees on 2011-04-25
> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.

This was one of the most helpful yet absurdly simple things I've run into today while tinkering in my new Ubuntu MacBook :D

Thanks, although this thread is a bit old.

---

### Post by Happy1789 on 2011-06-02
> **darolu said:**
> It is not necessary to add Medibuntu's repositories to get libcss, it is in the Ubuntu repositories.
If you haven't installed it, install the ubuntu-restricted-extras package and then install the libcss:

```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```If you use Kubuntu or Xubuntu just change it to kubuntu-restricted-extras or xubuntu-restricted-extras.

Thank you !
The first command line displayed a license agreement about using the library at the end with <Ok> in the terminal : it took me some time to understand and find out that to validate it the Tab button has to be pressed before pressing the Enter button on the keyboard... ;)
It works fine now !

---

### Post by darren123web on 2011-06-12
Smashing thanks guys - 

1st I ran the long command, but same problem,

2nd I ran the 2 short commands, 

bingo.

---

### Post by lisati on 2011-06-12
I think something was changed a few releases back, making the two-liner a lot easier than the jumping through hoops that was sometimes needed with older versions of Ubuntu.

---

### Post by idoisler on 2011-08-12
Might be over kill, but I did the same thing and it workes....

---

### Post by markinder on 2011-10-31
Thanks for that!  Worked perfectly on 11.04

M

---

### Post by Scard on 2011-12-28
very helpful.

thank you

---

### Post by oldos2er on 2011-12-28
Hush, hush, now you sleep.

---

