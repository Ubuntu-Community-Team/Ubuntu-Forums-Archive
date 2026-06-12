---
title: "How do I install Firefox 4 on ubuntu 8.04?"
date: 2011-03-26
forum: General Help
---

### Post by madelman on 2011-03-26
I have not found any information on how to install Firefox 4 on ubuntu 8.04.


Is it possible? or is it other "upgrade" ubuntu version issue?.

---

### Post by tredegar on 2011-03-26
8.04 with a GUI is past its sell by date.
OK for *servers* for another year or two though.

So it's time to install a newer version (10.10) and test that out.

Backup all of your home before you do this. You will need your personal files to be re-instated.

11.04 is supposed to be ready some time next month, but give 10.10 a try meanwhile.

---

### Post by Frogs Hair on 2011-03-26
I don't if 8.04 is included with this PPA or if you will have to install via the web site.```
sudo add-apt-repository ppa:mozillateam/firefox-stable
``````
sudo apt-get update
``````
sudo apt-get install firefox
```

---

### Post by madelman on 2011-03-27
> **Frogs Hair said:**
> I don't if 8.04 is included with this PPA or if you will have to install via the web site.```
sudo add-apt-repository ppa:mozillateam/firefox-stable
``````
sudo apt-get update
``````
sudo apt-get install firefox
```

sudo add-apt-repository returns: command not found

---

### Post by madelman on 2011-03-27
> **tredegar said:**
> 8.04 with a GUI is past its sell by date.
OK for *servers* for another year or two though.

So it's time to install a newer version (10.10) and test that out.

Backup all of your home before you do this. You will need your personal files to be re-instated.

11.04 is supposed to be ready some time next month, but give 10.10 a try meanwhile.


Yes, I think it is time to update. Thank you.

---

### Post by mpts on 2011-04-11
> **tredegar said:**
> 8.04 with a GUI is past its sell by date.
OK for *servers* for another year or two though.

So it's time to install a newer version (10.10) and test that out.

Backup all of your home before you do this. You will need your personal files to be re-instated.

11.04 is supposed to be ready some time next month, but give 10.10 a try meanwhile.

First, 8.04 is still officially supported (till the end of April 011, so we have about three weeks left), second, the question was how to install FF 4 on U 8.04, not whether U 8.04 is or is not &quot;correct&quot; distribution and definitely not when anyone should install whatever newer distro.

So, does please anybody know whether there are any repository available? The way by Frogs Hair doesn't work on U 8.04. Thx.

---

### Post by oldos2er on 2011-04-11
Have you tried downloading and running it? That might give the quickest answer to your question. Extract it to your home folder and double-click 'firefox'.

The mozillateam PPA is only available for 10.04 and 10.10.

---

### Post by Frogs Hair on 2011-04-11
> **mpts said:**
> First, 8.04 is still officially supported (till the end of April 011, so we have about three weeks left), second, the question was how to install FF 4 on U 8.04, not whether U 8.04 is or is not &quot;correct&quot; distribution and definitely not when anyone should install whatever newer distro.

So, does please anybody know whether there are any repository available? The way by Frogs Hair doesn't work on U 8.04. Thx.

I was uncertain if that PPA would work for 8.04 , it is the PPA being used on newer versions of Ubuntu. If the first command failed it is because there is no repository for 8.04 included with that PPA.

---

### Post by Enigmapond on 2011-04-11
Why not just do a fresh install of 10.10 now and save yourself all the headache?

---

### Post by mpts on 2011-04-11
> **oldos2er said:**
> Have you tried downloading and running it? That might give the quickest answer to your question. Extract it to your home folder and double-click 'firefox'.

The mozillateam PPA is only available for 10.04 and 10.10.

You mean vanilla Firefox, I suppose. Well, I am using this one on 32-bit Ubuntu, but there is none for 64-bit, whereas Ubuntu makes 64-bit versions.

---

### Post by lithopsian on 2011-04-11
Download [tarball from Mozilla]("http://download.mozilla.org/?product=firefox-4.0&os=linux&lang=en-US").  Untar in some handy place like /opt and run the firefox binary (or the firefox script).

I think it is unlikely you'll find a PPA for hardy offering Firefox although very probably you could install from a Lucid PPA since Firefox dependencies are very loose.  I don't know whether the Ubuntu builds might have been based on newer libraries or used install features that Hardy doesn't have.

The massively impatient forum geeks are recommending you upgrade to a product with a short lifetime (10.10) or one that isn't even released yet (11.04) but I suspect you prefer not to upgrade unless necessary.  If and when you do choose to upgrade, 10.04 might be a better idea since it will still be supported when 10.10 is dead and buried.

---

### Post by oldos2er on 2011-04-11
> **mpts said:**
> You mean vanilla Firefox, I suppose. Well, I am using this one on 32-bit Ubuntu, but there is none for 64-bit, whereas Ubuntu makes 64-bit versions.

64-bit Firefox 4.0 is here: [ftp://ftp.mozilla.org/pub/firefox/releases/4.0/linux-x86_64/en-US/](ftp://ftp.mozilla.org/pub/firefox/releases/4.0/linux-x86_64/en-US/)

---

### Post by mpts on 2011-04-12
> **oldos2er said:**
> 64-bit Firefox 4.0 is here: [ftp://ftp.mozilla.org/pub/firefox/releases/4.0/linux-x86_64/en-US/](ftp://ftp.mozilla.org/pub/firefox/releases/4.0/linux-x86_64/en-US/)

Thanks. I've tried it, but it doesn't work well. Reordered my bookmarks, displaying is buggy (part of the page scrolls whilst other part doesn't, or does different amount) &c.

I suppose I'll have to wait till I have time to reinstall the OS. It's kinda sad though: this morning I updated Opera from their repository, which works for U 8.04 normally, whereas OpenSource flagship Firefox is unsupported just because my installed distro is not the brand new shiny just brought home one.

---

### Post by Script Warlock on 2011-04-12
perhaps you can make a portable firefox to run on a usb stick...

---

### Post by dkbiby on 2011-04-13
As another user posted I extracted the tarball from Mozilla's site and just run it straight from there.  I also tried ([http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)) ubuntuzilla.py which worked previously for 3.5 but it is not working for 4.

I tried adding the repository for lucid and all went well until I tried to start firefox and it failed to open past asking if I wanted to install any addons.

The best solution would be a ([http://support.mozilla.com/en-US/questions/803624](http://support.mozilla.com/en-US/questions/803624)) .deb file like chrome.</a>

---

### Post by trainrabbit on 2011-08-15
I'd the same problem to here...
if that possible to install firefox 4.0 on ubuntu 8.04.
the problem why i didn't upgrade to ubuntu 11.04 its because i'm using Ncomputing card that only support to ubuntu 8.04.
Tq.

---

