---
title: "Doesn't download or install programs properly"
date: 2010-02-01
forum: General Help
---

### Post by dynamic.flare on 2010-02-01
I'm having a problem with downloading and installing programs.  I'm trying to play dvd's and have tried installing the plugins for the movie player that comes with the ubuntu.  It's not working.  I then tried downloading vlc media player.  It installed it but when I try to run it, it won't work.  There's no error message or anything.  It just doesn't open.  I'm kind of a noob so I'd appreciate any help.

Thanks!

---

### Post by iMisspell on 2010-02-01
Posting how you downloaded and installed the programs will help people help you.

Are you doing so by going to a web site and downloading the program.
or
Using command-line 'aptitude install' or 'apt-get'
or
Synaptic

Also posting the version of Ubuntu will help too.

---

### Post by t4thfavor on 2010-02-01
Try executing vlc from the commandline, and see if you get any errors there.

If so post them back here.

You may also have to do this in order to play DVD's properly.
```

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by dynamic.flare on 2010-02-01
This is what I get when I try to do that.

phoenix@phoenix-laptop:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread4 has no installation candidate


I used the apt-get command to install the programs.

---

### Post by dynamic.flare on 2010-02-01
and it's ubuntu 9.10 for laptop

---

### Post by t4thfavor on 2010-02-01
Mind doesn't do that, perhaps its libdvdcss2 for you, anybody else know a good dvd playback tutorial?

---

### Post by dynamic.flare on 2010-02-01
So somehow, I got it all to work...

I followed some instructions which involved removing the vlc player and all add-ons and then adding a multiverse mirror to my source list file.  Then I reinstalled another version of the player.  Used the commands the other person listed above, restarted the computer and now it works.


The only problem is that once I put the dvd into my laptop, I can't get it out.  The computer like freezes the dvd drive for some reason.  Is this an ubuntu issue or is it the dell laptop issue??

---

