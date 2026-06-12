---
title: "Cannot take screenshots in Firefox of WordPress sites"
date: 2011-06-03
forum: General Help
---

### Post by Paddy Landau on 2011-06-03
I sometimes take screen shots of websites in Firefox. The easiest way is to use one of the many extensions, e.g. [Screengrab]("https://addons.mozilla.org/en-US/firefox/addon/screengrab/").

However, I have discovered that, when trying to take a screen shot of the entire web page, the lower part of the page is not captured. This happens on [WordPress sites]("https://wordpress.com/") and, curiously, on [Mozilla's own results pages]("https://addons.mozilla.org/en-US/firefox/search/?q=screenshot&cat=all&x=0&y=0"). Other pages seem to be unaffected.

However, on Chromium, it works perfectly. (I will use this workaround for now.)

A friend, using the default installation of Firefox, has the same problem.

Any idea how to fix this screen shot problem? I've Googled but found nothing.

System: Ubuntu Lucid 10.04.
Firefox: 4.0.1

---

### Post by blueridgedog on 2011-06-03
Can you post an example?

---

### Post by Paddy Landau on 2011-06-03
Taking a page more-or-less at random from Google:
[http://education.usgs.gov/](http://education.usgs.gov/)
See the attached screen shot, which works.

Taking a page more-or-less from [WordPress]("http://wordpress.com/"):
[http://sleepwalkingintokyo.wordpress.com/2011/06/01/park-benches/](http://sleepwalkingintokyo.wordpress.com/2011/06/01/park-benches/)
See the attached screen shot, where most of the page is not saved.

In both cases, I used the Firefox add-on [Screengrab]("https://addons.mozilla.org/en-US/firefox/addon/screengrab/"), choosing the option Save > Complete Page/Frame. I get the same results with a number of other screen shot extensions.

---

### Post by Frogs Hair on 2011-06-03
The Gnome screen shot tool  is working on WordPess ; however , I did get a  invalid certificate warning from one of the links on the main page . When I went back to the page the link was gone.

---

### Post by Paddy Landau on 2011-06-03
Unfortunately, the Gnome Screenshot tool does not take the entire web page when it is longer than the screen.

---

### Post by lovinglinux on 2011-06-03
I was a Screengrab user, but I am currently using [Awesome Screenshot]("https://addons.mozilla.org/en-US/firefox/addon/awesome-screenshot-capture-/"). I recommend it.

Test it, and let me know if it solves the problem or not.

---

### Post by Paddy Landau on 2011-06-04
> **lovinglinux said:**
> I was a Screengrab user, but I am currently using [Awesome Screenshot]("https://addons.mozilla.org/en-US/firefox/addon/awesome-screenshot-capture-/"). I recommend it.

Test it, and let me know if it solves the problem or not.
Thanks for the idea. I have tried several different add-ons, including Awesome Screenshot (I agree, it's a good extension). They all give identical results.

I take it that you don't get that problem?

I deleted my Mozilla prefix and reinstalled the add-ons, in case it was a prefix corruption, but unfortunately that did not help.

---

### Post by lovinglinux on 2011-06-04
> **Paddy Landau said:**
> Thanks for the idea. I have tried several different add-ons, including Awesome Screenshot (I agree, it's a good extension). They all give identical results.

I take it that you don't get that problem?

I deleted my Mozilla prefix and reinstalled the add-ons, in case it was a prefix corruption, but unfortunately that did not help.

I don't get that problem. However, I am runing Kubuntu 11.04.

Have you tried to install only the screenshot add-on?

Have you tried to disable Compiz?

---

### Post by Paddy Landau on 2011-06-04
Oh, no! It's happening on more sites, now. Look at what happens on this very page (see attached screen shot).

---

### Post by Paddy Landau on 2011-06-04
> **lovinglinux said:**
> Have you tried to install only the screenshot add-on?
Yes, I did.

> **lovinglinux said:**
>  Have you tried to disable Compiz?
It's already disabled; my computer is a bit too slow with Compiz on.

---

### Post by lovinglinux on 2011-06-04
> **Paddy Landau said:**
> Yes, I did.


It's already disabled; my computer is a bit too slow with Compiz on.

Take a new screenshot from the wordpress page you used as an example, that has several photographs. But before taking the screenshot, scroll down a little bit in order to make two pictures visible in the screen. Let's see if they both appear in the screenshot and the others not or only the first is captured like the attached example.

---

### Post by lovinglinux on 2011-06-04
Can you upload that screenshot of this thread with original size?

You can use [http://picturepush.com/upa](http://picturepush.com/upa) for the upload.

---

### Post by Paddy Landau on 2011-06-04
> **lovinglinux said:**
> Take a new screenshot from the wordpress page you used as an example, that has several photographs. But before taking the screenshot, scroll down a little bit in order to make two pictures visible in the screen. Let's see if they both appear in the screenshot and the others not or only the first is captured like the attached example.
I have done that. It makes absolutely no difference. I have a sneaking suspicion it has something to do with Flash or objects, but of course I could be wrong.

> **lovinglinux said:**
> Can you upload that screenshot of this thread with original size?
 [The original sized picture.]("http://www3.picturepush.com/photo/a/5795226/img/5795226.jpeg")

---

### Post by Rachel5000 on 2011-06-04
[SIZE=3]*I[FONT=Times New Roman] use the standard Screenshot accessory in Ubuntu. I'm using Ubuntu 11.04[/FONT]*[FONT=Times New Roman] **(LOVE IT!**) [I]and previously used 10.04 & 9. something, but I get everythang. No problems..

Have you tried just  using the one that comes with OS?

I love to get pics from NatGeo, and have them printed up at walmart, really big like 22x36 or something. They make** AWESOME & WONDERFUL gifts**. Pick out a pretty frame and your friends will think you really luv em'.

Hope this helps,
Rachel[/I][/FONT][/SIZE]

---

### Post by lovinglinux on 2011-06-04
> **Rachel5000 said:**
> [SIZE=3]*I[FONT=Times New Roman] use the standard Screenshot accessory in Ubuntu. I'm using Ubuntu 11.04[/FONT]*[FONT=Times New Roman] **(LOVE IT!**) [I]and previously used 10.04 & 9. something, but I get everythang. No problems..

Have you tried just  using the one that comes with OS?

I love to get pics from NatGeo, and have them printed up at walmart, really big like 22x36 or something. They make** AWESOME & WONDERFUL gifts**. Pick out a pretty frame and your friends will think you really luv em'.

Hope this helps,
Rachel[/I][/FONT][/SIZE]

Problem is that, as far as I know, it can't capture the whole page that isn't visible on the screen.

---

### Post by lovinglinux on 2011-06-04
> **Paddy Landau said:**
> I have done that. It makes absolutely no difference. I have a sneaking suspicion it has something to do with Flash or objects, but of course I could be wrong.

 [The original sized picture.]("http://www3.picturepush.com/photo/a/5795226/img/5795226.jpeg")

How did you install Firefox 4.0.1? Have you tried to download from Mozilla, extract it and execute it from your home folder, just to see if the problem is with your Firefox installation?

---

### Post by linuxinstalledfromhdd on 2011-06-04
Try adding the PPA and upgrading your system:

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get remove firefox
sudo apt-get install firefox
sudo apt-get upgrade

---

### Post by coldraven on 2011-06-04
AFAIK you cannot grab what is not on the screen.
Solution, buy a really big screen! :)
Or, as I do in Firefox, File>Save page as.

---

### Post by Paddy Landau on 2011-06-04
> **Rachel5000 said:**
> I use the standard Screenshot accessory...
Unfortunately, it captures only what is on your screen, not the entire web page.

> **lovinglinux said:**
> How did you install Firefox 4.0.1? ...> **linuxinstalledfromhdd said:**
> Try adding the PPA and upgrading your system...
I used the PPA method as described. I understood that the PPA provides the same version as provided by the download, but of course in a deb format (the manual download comes in a tar).

I think it relevant that my friend, who still uses the default version that comes with Ubuntu (I think it's 3.6), has the same problem.

> **coldraven said:**
> AFAIK you cannot grab what is not on the screen.
Yes, you can! (Well, unless you have my problem, which started only recently.) Use any of the screen shot extensions (available for both Firefox and Chromium).

---

### Post by lovinglinux on 2011-06-04
Have you tested to see if Chromium exhibits the same problem?

I know that you have already tested on a clean profile. Try again, but this time, disable *Global Menu Bar Integration* extension.

---

### Post by Paddy Landau on 2011-06-04
> **lovinglinux said:**
> Have you tested to see if Chromium exhibits the same problem?
Yes, I mentioned this in the OP. Chromium works correctly with the Screengrab extension, so it's clearly Firefox (or something within Firefox).

> **lovinglinux said:**
>  I know that you have already tested on a clean profile. Try again, but this time, disable *Global Menu Bar Integration* extension.
I do not have such an extension. Does it come with the default Ubuntu installation?

---

### Post by lovinglinux on 2011-06-04
> **Paddy Landau said:**
> I do not have such an extension. Does it come with the default Ubuntu installation?

Oops, sorry. It comes only in Natty Narwhal.

---

### Post by lovinglinux on 2011-06-04
Okay, lets try something else.

Create a new Ubuntu account, log in with it, start Firerfox, install Screengrab and take a screenshot.

---

### Post by irv on 2011-06-04
Just for the record I am running xubuntu 11.04, Xfce DE and FF 4 with Awesome and here is what I get:
[ATTACH]194196[/ATTACH]
If you zoom in on it the whole page is there but very blur. What good is getting the whole page if you can't read it?

---

### Post by Paddy Landau on 2011-06-04
> **irv said:**
> Just for the record I am running xubuntu 11.04, Xfce DE and FF 4 with Awesome and here is what I get...The same as me, then.

> **irv said:**
> If you zoom in on it the whole page is there but very blur. What good is getting the whole page if you can't read it?Something about the way you saved it is wrong. The default settings save it full resolution.

Or, you did not check the original but only the uploaded version; when you upload to Ubuntu Forums, it will be reduced (with consequent loss of resolution) if taller than 1024 pixels.

> **lovinglinux said:**
> Create a new Ubuntu account, log in with it, start Firerfox, install Screengrab and take a screenshot.Same result, unfortunately.

It looks as though several people get this problem. Where do you suppose the right place would be to file a bug? It's tempting to do so for one of the extensions, but that's not quite right is it?

---

### Post by lovinglinux on 2011-06-04
> **Paddy Landau said:**
> Same result, unfortunately.

It looks as though several people get this problem. Where do you suppose the right place would be to file a bug? It's tempting to do so for one of the extensions, but that's not quite right is it?

Hard to tell. I would start searching bugzilla and launchpad to see if anyone else has a similar issue.

---

### Post by Paddy Landau on 2011-06-07
I have not found the issue reported elsewhere. I have [asked this question]("http://forums.mozillazine.org/viewtopic.php?f=9&t=2221361") on the Mozilla forums.

---

### Post by Paddy Landau on 2011-06-09
I have filed a [screenshot bug on Mozilla]("https://bugzilla.mozilla.org/show_bug.cgi?id=663135") for this problem.

---

