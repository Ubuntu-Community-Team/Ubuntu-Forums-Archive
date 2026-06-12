---
title: "How to install rhythmbox from ubuntu 10.10 (Maverick Meerkat) ?"
date: 2010-09-16
forum: General Help
---

### Post by Rushyang on 2010-09-16
Bonjour guys,

I came to know about some cool features from maverick meetkat. Oe of them is all new improved rythmbox. I watched it's screenshots and it really looks pretty interesting.

Now, How do I install it in Lucid Lynx? I came to this[ web tutorial, ]("http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html")

but by following that, It will update all the current updates, and I don't  want to do that. I ONLY want to install new rhythmbox. ie downloading it's gz etc.

---

### Post by andrewthomas on 2010-09-16
[http://packages.ubuntu.com/maverick/rhythmbox](http://packages.ubuntu.com/maverick/rhythmbox)
[B]
Read the entire page and make sure you can satisfy all dependencies.[/B]

---

### Post by Rushyang on 2010-09-16
I downloaded it, It's of just 1 MB. But when I open it , nothing 2 bars are filled very fast then nothing happens.. 

Any reason why it's not being updated?

---

### Post by uRock on 2010-09-16
Moved to MM Testing and Discussion.

---

### Post by zika on 2010-09-16
> **uRock said:**
> Moved to MM Testing and Discussion.Isn't this a Lucid "problem"...? It might be more interesting for Lucid users than here for us Maverick(s)... :)

---

### Post by uRock on 2010-09-16
> **zika said:**
> Isn't this a Lucid "problem"...? It might be more interesting for Lucid users than here for us Maverick(s)... :)
Thanks for pointing that out. Moved back to general help, though I was thinking the folks in the MM section would know best on how to do what the OP wants to accomplish.;)

---

### Post by zika on 2010-09-16
> **uRock said:**
> Thanks for pointing that out. Moved back to general help, though I was thinking the folks in the MM section would know best on how to do what the OP wants to accomplish.;)I'm afraid that there are too many dependencies that need to be met, so... It's just my uninformed and uneducated guess... :)

---

### Post by nilarimogard on 2010-09-16
Actually, you can. See [this]("http://www.webupd8.org/2010/09/rhythmbox-0131-has-been-released-and.html").

---

### Post by mc4man on 2010-09-16
> I came to this web tutorial,

but by following that, It will update all the current updates, and I don't want to do that. I ONLY want to install new rhythmbox

If you wish the newer rhythmbox in lucid the you'll need to upgrade several libraries, the ppa mentioned seems to work well and will provide those packages for you.
Otherwise I'm not sure I see the point. ( and some of what you might get in maverick isn't likely to work in lucid atm (or ever),, like the sound menu integration.

Whether you need all the possible upgraded packages from the ppa, not sure, could easily be found out.

Having a lucid install I'm no longer using went ahead and added the ppa and updated all the packages it provided - 23 here.

All seems fine, though I'd do slightingly differently (and may not matter.

First I'd update lucid fully, then add the ppa and run an update.
Update manager had no issue installing all the upgraded packages - see screen.
sudo apt-get upgrade balked on a number, though possibly 2 runs thru would have resolved.
>  sudo apt-get upgrade
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libglib2.0-0 libglib2.0-data libglib2.0-dev libvala0 rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins valac
The following packages will be upgraded:
  cdbs libdbusmenu-glib-dev libdbusmenu-glib1 libdbusmenu-gtk1 libglib2.0-doc
  libgtksourceview2.0-0 libgtksourceview2.0-common libindicate-gtk2
  libindicate4 libtotem-plparser-dev python-indicate python-webkit
12 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 4,521kB of archives.
After this operation, 3,506kB of additional disk space will be used.
Do you want to continue [Y/n]? n

I'd also install ppa-purge in case there is an issue or you wanted to revert for some reason. 

(personally I'm much happier w/ maverick

---

### Post by zika on 2010-09-17
> **nilarimogard said:**
> Actually, you can. See [this]("http://www.webupd8.org/2010/09/rhythmbox-0131-has-been-released-and.html").I'm, sort of, glad I was wrong... Cool!

---

