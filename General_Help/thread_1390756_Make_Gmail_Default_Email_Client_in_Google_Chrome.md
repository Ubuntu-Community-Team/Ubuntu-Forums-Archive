---
title: "Make Gmail Default Email Client in Google Chrome"
date: 2010-01-26
forum: General Help
---

### Post by afbase on 2010-01-26
Hi,

My preference for Chrome over Firefox and other browsers leaves me to a small but fine feature I've had in Firefox... have Gmail as the default email client in google chrome.

[This link](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/) showed how to do exactly this in firefox.
  How do I do it in google Chrome?

---

### Post by raktarok on 2010-01-26
This should do the trick for all browsers. Install the deb file from this link:

[http://sourceforge.net/projects/gnome-gmail/files/](http://sourceforge.net/projects/gnome-gmail/files/)

Enjoy!

---

### Post by afbase on 2010-01-26
> **raktarok said:**
> This should do the trick for all browsers. Install the deb file from this link:

[http://sourceforge.net/projects/gnome-gmail/files/](http://sourceforge.net/projects/gnome-gmail/files/)

Enjoy!

You are AWESOME!:popcorn:

---

### Post by slamMaster on 2010-02-12
Thanks a ton, that was beginning to bug me.

Just a note to others that this only adds gmail to the list of preferred email clients.  Go to System > Preferences > Preferred Applications to change from evolution to gmail.

---

### Post by jaricanese7 on 2010-02-15
Yes yes thank you very much. Worked like a charm and is exactly what I wanted. I found other ways to make Gmail the default client but those opened it through Firefox, now I can use it through Google Chrome.

---

### Post by ElSlunko on 2010-03-15
Just found this app in a lifehacker post made today (the gnome-gmail one).

It's pretty damn cool so I thought this thread was worth a mega-bump.

[http://lifehacker.com/5493654/gnome-gmail-tightly-integrates-gmail-into-linux-desktops](http://lifehacker.com/5493654/gnome-gmail-tightly-integrates-gmail-into-linux-desktops)

---

### Post by Steffan.carlos on 2010-08-12
AWESOME!!! Thanks guys this is perfect still works in 10.04. Good Work

---

### Post by Altimos on 2010-09-09
awesome guys! this just makes chrome that much better.

---

### Post by tamccullough on 2010-10-22
Cheers, worked for me too.
I think I am going to be going the route of eliminating the use of thunderbird and/or evolution.
Much less hassle I think.

---

### Post by jwilker2 on 2010-12-13
Awesome extension to gnome!
Thanks for the effort...

---

### Post by slorge on 2011-01-05
works in 10.10, too!  thanks bunches!

---

### Post by fenzik on 2011-02-25
Awesome..!

---

### Post by lifelike27 on 2011-04-13
I just wanted to note that currently in Ubuntu 11.04 (Beta 1), you can only choose installed email clients. The 'custom' option is no longer there.

---

### Post by quick_nick on 2011-04-24
> **lifelike27 said:**
> I just wanted to note that currently in Ubuntu 11.04 (Beta 1), you can only choose installed email clients. The 'custom' option is no longer there.

Yeah I know.  That really blows.  Anyone know a fix around this?  Why would they limit us like that?

---

### Post by vonedaddy on 2011-04-26
You can use a simple bash script to accomplish this without installing anything.  The below instructions are for someone using know, but as long as you can set your default mail app in the OS your good to go.


[http://www.putorius.net/2011/04/make-gmail-your-default-email-in-chrome.html](http://www.putorius.net/2011/04/make-gmail-your-default-email-in-chrome.html)

---

### Post by TryMe on 2011-05-11
> **lifelike27 said:**
> I just wanted to note that currently in Ubuntu 11.04 (Beta 1), you can only choose installed email clients. The 'custom' option is no longer there.

This is still true in the released current natty 11.04. Sadly it seems that it's a bug that has been given importance:Undecided &#8594; Low . see launch pad report [https://bugs.launchpad.net/ubuntu/natty/+source/gnome-control-center/+bug/708382]("https://bugs.launchpad.net/ubuntu/natty/+source/gnome-control-center/+bug/708382")

and here:[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/729603]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/729603")

Maybe if we all let it be known it does bother/effect us the control center project may change their mind. Besides what if you did not like gmail and wanted yahoomail or any terminal based mail client.

---

### Post by Automat2 on 2011-06-29
> **TryMe said:**
> 
Maybe if we all let it be known it does bother/effect us the control center project may change their mind. Besides what if you did not like gmail and wanted yahoomail or any terminal based mail client.

There are some newer messages now. But I wrote mine too. Maybe one day we had the option restored in "Preferred Applications".

---

### Post by trien on 2011-08-08
In Firefox.Edit-Preferences-Applications-mailto-use gmail

---

### Post by fox mulder on 2011-08-30
thanks this had really been bothering me

---

### Post by jajodo on 2011-09-05
> **quick_nick said:**
> Yeah I know.  That really blows.  Anyone know a fix around this?  Why would they limit us like that?

> **vonedaddy said:**
> You can use a simple bash script to accomplish this without installing anything.  The below instructions are for someone using know, but as long as you can set your default mail app in the OS your good to go.


[http://www.putorius.net/2011/04/make-gmail-your-default-email-in-chrome.html](http://www.putorius.net/2011/04/make-gmail-your-default-email-in-chrome.html)

I used the gnome-gmail package for simplicity.  I had to use the latest version from sourceforge.

As an alternative you might be able to make and call a script as above.  Since the custom option is no longer available in preferred apps I wonder if gconf could be used:

run gconf-editor
- Go to /desktop/gnome/applications/url-handlers/mailto
- Right-click &#8220;command&#8221; field, Click on &#8220;Edit Key&#8221; and modify to *pathtoyourscript*

Then click enabled, unclick needs terminal.

I have not tried it yet but it seems like it should work.
gnome-gmail is actually listed under "command" on my system since I installed the package but I am using Linux Mint which is based on 11.04 but still Gnome 2

---

### Post by h0bbe on 2011-10-31
I use Firefox as my default browser but want to use Chromium for Gmail. Ist it possible to set gnome-gmail up to open Gmail in Chromium (app mode) despite it's not my default browser?

---

### Post by afbase on 2011-10-31
Have you tried it with the latest version?
 
If I were you, make a new post and reference this post if you feel that it is necessary to explain your issue.
 
GNOME 3 was released after this thread was marked [Solved].  I am not sure if this thread is still applicable or not for chromium or chrome since I was using GNOME 2.  I don't know if that version change makes a difference.

---

### Post by psb777 on 2011-12-31
This is no longer SOLVED in the latest Ubbuntu. Please let's remove the "[SOLVED]" text from the subject or make the subject version specific.

---

### Post by fragos on 2011-12-31
Gnome-gmail from the Software Center has worked for me. I seem to remember running gconf-editor and in desktop -- gnome -- url-handlers -- mailto, I set command to "gnome-gmail %s". Check to see if that's properly set on your system.

---

