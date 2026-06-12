---
title: "Gnome-do and Firefox 3.5"
date: 2009-07-01
forum: General Help
---

### Post by alligoodw on 2009-07-01
I've installed Ubuntu 9.04 on my laptop.  I've downloaded Firefox 3.5 and manually installed it - it's working fine and I've loaded it in the main menu.  

My question is this:  How do I get Gnome-do to run the manual installation of Firefox 3.5 as opposed to the default Firefox 3.0.11?  I'm sure it is simple, but I don't know the mechanics of Gnome-do.

---

### Post by nothingspecial on 2009-07-02
I would like to know the answer to this also

---

### Post by moster on 2009-07-02
If you really install it and not just unpack it and run it from there.. you can type "firefox-3.5" in gnome do or in terminal.

:)

When next version come, or you just want to try beta in safe way. Download .tar.bz2 unpack it to somewhere not important, and run shell script in that directory. You find it using detail view in nautilus, it will be called firefox-3.6 or just firefox..

---

### Post by alligoodw on 2009-07-02
All I want to know is how do I get Ubuntu 9.04 to recognize Firefox 3.5 as my default browser and not Firefox 3.0.11 . . . it's that simple.

Another thing too . . . if I try and uninstall Firefox 3.0.11, Synaptic removes Sun's Java plugin with it.  If I try and reinstall Sun's Java plugin, it automatically re-installs Firefox 3.0.11.  I don't need both Firefox 3.5 and Firefox 3.0.11.

---

### Post by moster on 2009-07-02
hehe, Ok :)

Open your 3.5 version, go to preferences-advanced.

On bottom you see "always check that shiretoko is your defautl browser" and Check Now button. Click that button, answer the correct question and your problem is gone :)

---

### Post by alligoodw on 2009-07-02
I've already done that.  Still, Gnome-do loads Firefox 3.0.11 instead of Firefox 3.5.  Ubuntu isn't recognizing Firefox 3.5 as the default.  How do we fix that?

---

### Post by ChaiTan on 2009-07-02
Go to the Gnome System Menu->Preferences->Preferred Applications and change firefox to whatever you want, use custom command if firefox-3.5 is not listed.

---

### Post by Simian Man on 2009-07-02
Open a terminal and type 'which firefox'.  This will give you the location of the default firefox install.  Then type 'which firefox-3.5' which will give you the location of the new version.  Then you can replace the old one with a link to the new one.

I haven't tested this code (ues at your own risk) but it should give you an idea what I mean:
```

sudo ln -s `which firefox` `which firefox-3.5`

```

---

### Post by alligoodw on 2009-07-02
I've already done that.  Gnome-do still loads Firefox 3.0.11.  I'm sure the answer is simple; I've got to find the key, that one simple key to fix this problem.

---

### Post by Simian Man on 2009-07-02
OK, so I tried this and apparently ln complains if you try to replace an application with a link.  So assuming firefox is at /usr/bin/firefox, this code should work:

```

sudo su
mv /usr/bin/firefox /usr/bin/firefox-3.0
ln -s `which firefox-3.5` /usr/bin/firefox

```

This moves the old firefox to firefox-3.0 (in case you want it back later) and then links the command firefox to the new firefox 3.5.  That should fix your problem very thoroughly :).

---

### Post by moster on 2009-07-02
If I were you... I would remove every version of firefox from synaptic and associated libraries -restart- and then fresh install firefox 3.5 after.

There are some specific packages in synaptic like firefox-3.0-gnome-support if you leave then installed it can make problems for you.. that is why you need to check everything that has firefox in his name in synaptic.

After this clean, it cannot be anything left to jerk you a round.

After that, I recommend adding custom repositories if you do not already do that, and install 3.5 version from it.

When you look at my synaptic and search for firefox, you would find checked and installed only this:
-firefox-3.5
-firefox-3.5-branding
-firefox-3.5-gnome-support

---

### Post by alligoodw on 2009-07-02
When I get home this evening from work, I'll give it a try.  I'm very optimistic you know; I believe we'll whip this puppy yet!

---

### Post by romuald_geo on 2009-07-02
Try to use Ubuntuzilla.Its a script that downloads Mozilla Firefox 3.5 and replaces it with your version of Firefox and cleans up the installation
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by Dougie187 on 2009-07-02
You know you could simply type firefox into gnome-do, and press down to open the results window. Then see if there are other options besides the default firefox. There might be another one that has a name different than just Firefox. I'm not sure if this is correct or not, but I think gnome-do uses the "most used" link for each name that you type in, so even though you type in firefox, and you want to use 3.5, 3.0 is installed and has been used more, so it defaults to that. Though that DOESN'T make it your default browser.

I would check the results window, and then you could just make a link to it on gnome-do if you use docky, otherwise, you have to use it a few times to get it to be more popular than firefox. Alternatively you could uninstall 3.0, then the only one would be 3.5. Or you could change links as is mentioned.

---

### Post by alligoodw on 2009-07-02
Problem is resolved.  After installing ubuntuzilla and running it, it resolved all the problems I had.  I'm now running Firefox 3.5 and Ubuntu is seeing it as the true default.  See!  I told you it was going to be easy. 

I appreciate all the feedback I've received from all of you.  Thank you for your time and expertise.

---

### Post by moster on 2009-07-03
> **alligoodw said:**
> Problem is resolved.  After installing ubuntuzilla and running it, it resolved all the problems I had.  I'm now running Firefox 3.5 and Ubuntu is seeing it as the true default.  See!  I told you it was going to be easy. 

I appreciate all the feedback I've received from all of you.  Thank you for your time and expertise.
I am very happy for you but..

I am linux fan, but I find this kind of problems very, VERY discouraging. Just look at it from distance. Few more "experienced" people "helping" one one guy to make 3.5 version default.

We should not be even talking about trivial things like that. Ah, I am loosing my faith in linux :(

---

