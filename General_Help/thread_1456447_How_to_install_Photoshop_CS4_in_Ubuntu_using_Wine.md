---
title: "How to install Photoshop CS4 in Ubuntu using Wine?"
date: 2010-04-17
forum: General Help
---

### Post by chris.jericho on 2010-04-17
Hey there fellows...

I use Photoshop for photo editing and also for creating custom graphics. I recently switched to Ubuntu... since its free and great at the same time. 

But in Ubuntu I cannot install any Adobe softwares since it does not support it yet. I heard of a solution... some software called Wine that lets you install Windows softwares into Ubuntu....

I looked around for solution and how to use it.... but got confused and couldn't understand a work in those tutorials... since I am very new to Ubuntu.. 

Can anyone please help me and explain me in simple language on how can I install Photoshop in Ubuntu...

I am using Lucid Lynx... :) :)

---

### Post by d3v1150m471c on 2010-04-17
I don't know about cs4 but I've used cs2 before. It's not perfect but it worked. You'll probably need to acquire winetricks somewhere down the line if you want it to be "smoother" by adding things like fonts and whatnot.

Anywho... if you have the program open the installer with wine and you're good to go. If it gives you trouble try changing wine's version of windows with the little configuration thing it has. good luck.

---

### Post by chris.jericho on 2010-04-17
thanks for the reply bro.... I'll try and then reply back..... but I hope Photoshop CS4 will work....

---

### Post by 666f6f on 2010-04-17
Hey Chris,

First off, I wouldn't recommend Ubuntu Lucid Lynx, it's still in beta (i.e. not production ready) and you may experience problems that may disappoint you.

For instructions on how to install and use Wine you can refer to the [Ubuntu Wine Wiki]("https://help.ubuntu.com/community/Wine") and to the official [Wine FAQ]("http://wiki.winehq.org/FAQ").

To check if your application (Photoshop in this case) runs or not under Wine you can check it's compatibility status in [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true"). **UPDATE:** Photoshop CS4 [seems to work]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318") in Ubuntu 10.04 (but not under Ubuntu 9.10, so forget my comment in the beginning of my post!), but I haven't tried it my self.

If you have problems with Wine you can ask questions in the [Ubuntu Wine Forum]("http://ubuntuforums.org/forumdisplay.php?f=313").

Finally, there is at least one popular Photoshop alternative in Ubuntu that is called GIMP, you may want give that a try.

---

### Post by chris.jericho on 2010-04-17
Thanks for the reply bro...... I will go check out the Wine Docs...... 
I've used GIMP.... but I am used to photoshop and been working on it from the last 3 years.... 

anyways thanks for the reply :) :)

---

### Post by t0p on 2010-04-17
I was given a copy of Photoshop CS4, which I figured I ought to try and use (it was a gift after all).  I use a guest XP in VirtualBox to run Photoshop and a couple of other Winders apps.  Unfortunately Photoshop runs *very* slowly in VirtualBox - my machine has just 1 GB of RAM.  At some stage I plan to add another gig of RAM, maybe it'll run better then.

But in the meantime I use the Gimp.  I'm an enthusiastic amateur photographer and I use the Gimp just for basic darkroom operations (like dodging and burning) and a bit of cloning.  For simple operations like those the Gimp is fine.  So, unless you want to use some feature that the Gimp doesn't have, I recommend you at least give it a decent try.  The Gimp's native Linux version will, in my opinion, run quicker and far more smoothly than Photoshop in Wine or VirtualBox.

---

### Post by 666f6f on 2010-04-17
OK, hope it works for you. In case it doesn't work you can try an older version of Photoshop, for example [Photoshop 7 which seems to be well supported]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1336"). If you absolutely want to stick with CS 2.0, you can [run Windows in VirtualBox]("http://www.downloadsquad.com/2008/02/10/run-windows-in-a-virtual-machine-using-ubuntu-and-virtualbox/"), like t0p said, and install CS2 there.

---

### Post by chris.jericho on 2010-04-17
cool.... I'll give gimp a try,,...... since you've used it already.... does it.... have function like embossing, beveling, satin overlay.... those kind of photoshop live filters...... and other basic effects to give cooler styles... ????

---

### Post by Greg Xix on 2010-04-17
I assume the Wine you have installed is probably 1.0.1

Try using a later, development of version of Wine like 1.1.29 or 1.1.38



_***[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)***_

Download from the big bolded links, not the -dev links.

---

### Post by chris.jericho on 2010-04-17
okay.... so will these run photoshop Cs4 nicely??

---

### Post by chris.jericho on 2010-04-17
[@Greg Xix]("http://ubuntuforums.org/member.php?u=726859")

i hope those packages work on my 10.04 lynx

---

### Post by t0p on 2010-04-17
> **chris.jericho said:**
> cool.... I'll give gimp a try,,...... since you've used it already.... does it.... have function like embossing, beveling, satin overlay.... those kind of photoshop live filters...... and other basic effects to give cooler styles... ????

Here are some links to help you ascertain if the Gimp has the features you require: [[link1]("http://www.google.co.uk/#hl=en&newwindow=1&safe=off&q=gimp+embossing+beveling+satin+overlay&meta=&aq=&aqi=&aql=&oq=gimp+embossing+beveling+satin+overlay&gs_rfai=&fp=579125fd6573fbeb")] [[link2]("http://ihatehate.wordpress.com/2010/04/08/how-to-search-the-internet-3-how-to-actually-use-a-search-engine/")].

HTH.

---

### Post by Greg Xix on 2010-04-17
As 't0p' mentioned, VirtualBox uses a LOT of RAM in XP and its worse with Vista and 7. Dont know about Windows 2000.

Also, if you are going to use XP on VirtualBox, be sure to install SP3 for the XP. I had a lot of trouble installing and running different programs. On a hunch, I installed Service Pack 3 and most issues were resolved.

One last thing with VirtualBox is to NOT get the OSE(Open Source Edition), this is the version thats offered within the Ubuntu Software Center and is slightly limited.

Here is a "fuller" version:

***_[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)_***

Save the appropriate for your system .DEB and install.

---

### Post by chris.jericho on 2010-04-17
okay... i'll give it a try..... but i don't have xp.... i was using vista.... but it sucked so bad.... thats the reason I switched to Ubuntu.... as Windows vista sucks....

those links thats you had posted before... of the Wine software..... will they work on Lucid Lynx... beta 2

and then,   can that run CS4....
actually I don't wanna use Virtual box.... since it also make other applications slower

---

### Post by chris.jericho on 2010-04-17
[@t0p   ]("http://ubuntuforums.org/member.php?u=380385")

I can't understand the second link...... hows that related to Gimp...

of ihatehate.wordpress.com

---

### Post by Greg Xix on 2010-04-17
Yeah just download the .DEB files for 9.04, I tested it out on a live USB session before and it worked for me.

I had to install VirtualBox + Xp for 1 important program, as much as I hated doing it, because WINE didnt work. I have 2gb Ram and it does ok. So if you REALLY want to use CS4 within Ubuntu, you may have no choice. Hopefully you have more than 2gb of ram since you have Vista

---

