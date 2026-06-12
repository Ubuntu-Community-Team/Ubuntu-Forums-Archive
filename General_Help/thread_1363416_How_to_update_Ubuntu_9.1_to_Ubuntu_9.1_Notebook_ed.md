---
title: "How to update Ubuntu 9.1 to Ubuntu 9.1 Notebook edition"
date: 2009-12-24
forum: General Help
---

### Post by PinoyEngine™ on 2009-12-24
I am very very sad to know that after installing and being comfortable to my current ubuntu here in my notebook,
ubuntu just released their notebook edition.

i am really afraid for a reformat.

but, I am looking forward that there might be a fix that I can use to just update my current ubuntu to ubuntu notebook edition.

I am looking for any response.

merry christmas anywayz,

---

### Post by bodhi.zazen on 2009-12-24
Use the meta package :

```
sudo apt-get update && sudo apt-get install ubuntu-netbook-remix
```

[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

---

### Post by jerrylamos on 2009-12-24
> **bodhi.zazen said:**
> Use the meta package :

```
sudo apt-get update && sudo apt-get install ubuntu-netbook-remix
```

[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

apt-get "Couldn't find package ubuntu-notebook-remix".

Any ideas?

Oops, that package not on all mirrors.  Got it now.

Thanks, Jerry

---

### Post by bodhi.zazen on 2009-12-24
netbook not notebook =)

---

### Post by PinoyEngine™ on 2009-12-25
I just run that, it downloaded 16MB and is that it?

thanks.

---

### Post by bodhi.zazen on 2009-12-25
> **PinoyEngine™ said:**
> I just run that, it downloaded 16MB and is that it?

thanks.

I am not sure of the size of the download, but it is primarily an interface, and not much specific to netbooks, so give it a try =)

---

### Post by jerrylamos on 2009-12-25
I tried the remix .deb file on top of a fresh karmic 9.10 install.  It works sort of, with a mix of the standard gnome desktop and the remix desktop.  Rather confusing and not something I'd want to demonstrate ubuntu netbook to.

I'm trying a fresh download of netbook from 
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)
which is a development Alpha level lucid since the karmic level netbook didn't like my IBM Thinkpad T40.

Jerry

---

### Post by PinoyEngine™ on 2009-12-25
Ok, I think I have to install the full notebook remix.

btw, anyway I can restore my old ubuntu 9.1 from this patch?

---

### Post by Strongman332 on 2009-12-25
well if it work like adding Kubuntu to Ubuntu just change your session at the login screen. but i think you should Google it to besure

---

### Post by PinoyEngine™ on 2009-12-26
I can't see that option here.

help.

---

### Post by PinoyEngine™ on 2009-12-26
I think I need a bump here.

I really do not want to double post.

but, is there a way I can revert it back to normal ubuntu 9.10

---

### Post by spiderbatdad on 2009-12-26
There is supposed to be a switcher to allow you to choose between classic desktop and netbook, but my understanding is it was broken in 9.10, so IMO you should not have used the installation method, you used, but should have made a bootable usb or cd to try netbook remix. 
Can you simply remove it through synaptic as you installed it, without compromising your desktop? If you actually installed netbook remix by itself, then no. You will have to reinstall the desktop version.

---

### Post by PinoyEngine™ on 2009-12-26
ok, then I have to reinstall it then.

thanks!

Merry Christmas!

---

### Post by Strongman332 on 2009-12-29
you can disable it in startup applications

it is listed as netbook launcher and maximus

---

