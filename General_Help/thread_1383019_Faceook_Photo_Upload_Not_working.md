---
title: "Faceook Photo Upload Not working"
date: 2010-01-16
forum: General Help
---

### Post by myth01 on 2010-01-16
Hi all

I have Googled for an answer but not found anything that has helped my situation yet.

I'm running Google Chrome (4.0.249.43) on Ubuntu 9.10 and the photo uploader on Facebook always only produces a grey box.  Is this a problem with Java or just a standard issue with Ubuntu?

I had the same problem with Firefox.  A solution would be really helpful as this is driving my girlfriend nuts and she keeps having to use the Windows PC (urgh!)

---

### Post by myth01 on 2010-01-17
Bump.

I have now tried to use F-Spot to upload the pictures but that fails with the message:

Error Uploading to Facebook: Code: 1, message: An unknown error occurred

This is now becoming a Linux show-stopper with the girlfriend.

So is there *any* way to upload photos to Facebook with Ubuntu?

---

### Post by Uncle Spellbinder on 2010-01-17
No issues here. I click "use simple uploader" in Facebook. 

**_*That brings me to the file browser*_:**
[IMG]http://i45.tinypic.com/23uy9uq.jpg[/IMG]




**_*[I]Click "Browse" brings me to my pictures*[/I]_:**
[IMG]http://i45.tinypic.com/acenvo.jpg[/IMG]




**_*Choosing my picture shows up ready to upload*_:**
[IMG]http://i49.tinypic.com/nxnhgx.jpg[/IMG]




**_*Clicking "upload" and process completes as expected*_:**
[IMG]http://i48.tinypic.com/9u82s7.jpg[/IMG]




**_*Image is then available in album*_:**
[IMG]http://i45.tinypic.com/534410.jpg[/IMG]

---

### Post by myth01 on 2010-01-17
Cheers unclespellbinder for your response.  Unfortunately the simple uploader doesn't really cut it, with a limit of 5 pictures at a time, doing a full size album (60 photos) requires 12 trips round the process.

Surely this is one of those things that should 'just work'?

---

### Post by Uncle Spellbinder on 2010-01-17
> **myth01 said:**
> Surely this is one of those things that should 'just work'?

Probably so. But I've yet to have *_any_* java uploader work in Ubuntu. And I do have the latest Java installed. Though only 5 at a time is not the best of worlds. It's better than nothing.

---

### Post by apoth on 2010-01-17
I've used this project, it worked quite well:

[http://code.google.com/p/fb-photo-uploader/](http://code.google.com/p/fb-photo-uploader/)

---

### Post by Uncle Spellbinder on 2010-01-17
> **apoth said:**
> I've used this project, it worked quite well:

[http://code.google.com/p/fb-photo-uploader/](http://code.google.com/p/fb-photo-uploader/)Looks interesting, except for the statement at the top of the page...

[I]"This Uploader is no longer under active development due to lack of time. If anyone wants to take it over I can give you the project admin rights. 
This means that there will be no new releases for the foreseeable future.
I suggest you use [BLOOM](http://antaki.ca/bloom/) instead"[/I]

May give it a try, nonetheless.

---

### Post by drewsus on 2010-01-17
have you installed these packages?

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
```
Try that and report back

---

### Post by Uncle Spellbinder on 2010-01-17
> **drewsus said:**
> have you installed these packages?

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
```
Try that and report back

As I said above in post #5, I have the latest java installed...

```
unclespellbinder@wombat:~$ sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jdk is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
unclespellbinder@wombat:~$ 
```

Still, no java uploaders work at all.

---

### Post by myth01 on 2010-01-17
> **drewsus said:**
> have you installed these packages?

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
```
Try that and report back

I tried this and everything but the jdk and fonts packages were already installed.  I let them install but still no joy, only a grey box.

---

### Post by drewsus on 2010-01-17
hmm sorry thats all I got right now. The uploader works fine for me in Firefox and Chrome in 9.10. 
I can't think of anything else that I did.

---

### Post by Uncle Spellbinder on 2010-01-17
Yep. It's working in Firefox. I've been using SeaMonkey and for some reason It won't work. At least it's working in Firefox, though. I'll need to figure out the problem with SeaMonkey.

---

### Post by nanotube on 2010-01-19
just fyi:
just tested it on karmic, using the latest seamonkey (2.0.2) and the sun-java6-plugin from the repos, and the java photo uploader on facebook worked just fine.

if you're trying to use the old seamonkey1, that may be the problem. seamonkey1 is a really old codebase, and a lot of things tend to not work quite right on it.

---

### Post by myth01 on 2010-01-20
Thanks nanotube, got it working now but not quite sure how!

Here's what I did:
[LIST]
[*]Installed Seamonkey - tested java (Facebook Photo Uploader)and got Missing Plugin message.
[*]Clicked Install Plugins but only Manual Install available.
[*]Cancelled that and re-installed sun-java-jre and sun-java-plugin from synaptic.
[*]Checked Seamonkey again, still no java.
[*]Downloaded and installed Java from Sun/Java website (following all instructions including placing the sym link in the /usr/lib/mozilla folder)
[*]Checked Seamonkey again, Java worked!!
[*]Out of curiosity, checked Google Chrome again, and, Java worked!!  So not quite sure which step made Chrome work but now it works.
[/LIST]

Thanks to everyone, the Ubuntu forum has proven itself again.

---

### Post by nanotube on 2010-01-20
Hi myth01,

the initial java detection problems you've been having are due to this bug in the sun-java6-plugin package:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)
which fails to place the appropriate link in /usr/bin/mozilla/plugins

(see also the workaround included in the bug). reproducing it here for easy reference:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

the reason the java direct from sun worked, is that you manually placed the right symlink.

if you want, you could uninstall the sun stuff, and go back to the repositories - just don't forget the workaround of manually linking the plugin. 

just for future reference to everyone here. :)

and if this workaround works for you, then it wouldn't hurt to go to that launchpad bug and post a 'me too message'. that would help push it up the queue.

---

### Post by Maheriano on 2010-01-20
Trying this when I get home.

---

### Post by nanotube on 2010-01-20
> **Maheriano said:**
> Trying this when I get home.

and while we're at it:

and as far as installing the latest seamonkey: i recommend using the ubuntuzilla repository (if you're on 32bit ubuntu):
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by myth01 on 2010-01-20
Just had a look at the ubuntuzilla project website.  I didn't realise the versions of software like this weren't updated in the repos.  

I downloaded the Seamonkey tar direct from the Seamonkey website so is there much (any) difference to the one I could get from the ubuntuzilla repo?

I had a really quick play with Seamonkey and I was surprised by just how quick it is.  I've only just moved over to Chrome though and don't know if I can be bothered to move again so soon.  I also love how minimal the address bar/tabs are in Chrome.  I'm running on a 15inch laptop at the moment so screen space is vital, and I couldn't find a way to replicate Chrome's appearance in Seamonkey.

---

### Post by nanotube on 2010-01-20
> **myth01 said:**
> Just had a look at the ubuntuzilla project website.  I didn't realise the versions of software like this weren't updated in the repos.  

I downloaded the Seamonkey tar direct from the Seamonkey website so is there much (any) difference to the one I could get from the ubuntuzilla repo?


no difference - the ubuntuzilla repo just packages up the mozilla builds out of that same tar.gz.  

the benefits of getting it from the repo are:
(1) you get updates through the standard update-manager channel, rather than having to update it separately yourself.
(2) the menu item and various shortcuts are properly set up for you, so you don't have to do it manually.

but if you're happy running it from a tar.gz, nothing wrong with that.

---

### Post by axelswe on 2010-02-10
I found a fix/workaround for firefox

     [B]
THE FIX[/B]:
in the adressbar in firefox write: 
     
     ```
about:config 

```It will warn you not to screw around with the settings there in. ignore the warning =) and continue
In the **Filter** field write:
     
     ```
user 
``` This should narrow down your alternatives. Find the row that says:
**general.useragent.extra.firefox**
Rightclick it and choose "modify". Change the value from "Firefox/3.5.7" (in my case) to "Firefox/3.6.0" restart or reload Firefox and it should work!
                                                                                               ________________

---

### Post by jalirious on 2010-02-16
A simple and effective answer is bloom.

[http://antaki.ca/bloom/](http://antaki.ca/bloom/)

Very easy to use, runs on multiple platforms, uploads full albums and videos to facebook.

---

### Post by kittybrat on 2010-02-28
> **jalirious said:**
> A simple and effective answer is bloom.

[http://antaki.ca/bloom/](http://antaki.ca/bloom/)

Very easy to use, runs on multiple platforms, uploads full albums and videos to facebook.

I used to use Bloom, but it has since stopped working.  It will download, but the program never opens.  I don't know if it has to do with my upgrade to Jaunty or not, but, it just does not work.
Also, since Firefox refuses to load now, and I use Google Chrome, I have even more of a problem with java.

---

### Post by ouq77 on 2010-03-07
> **axelswe said:**
> I found a fix/workaround for firefox

     [B]
THE FIX[/B]:
in the adressbar in firefox write: 
     
     ```
about:config 

```It will warn you not to screw around with the settings there in. ignore the warning =) and continue
In the **Filter** field write:
     
     ```
user 
``` This should narrow down your alternatives. Find the row that says:
**general.useragent.extra.firefox**
Rightclick it and choose "modify". Change the value from "Firefox/3.5.7" (in my case) to "Firefox/3.6.0" restart or reload Firefox and it should work!
                                                                                               ________________

This worked for me, together with a whole lot of other suggestions (so not sure what exact change did the trick, but changing the user agent finally made it work)

---

### Post by hotweiss on 2010-03-07
I have the Java Facebook photo uploader working in Chrome.  What you have to do is open Firefox and then load a web page that requires Java and install Java through firefox.  When you open up Chrome, the Java uploader will be working.  Just give it some time to download the applet...

---

### Post by jalirious on 2010-03-18
@kittykat

- yes, quite. I did a fresh install of 9.10 yesterday, but cannot now install bloom, which was previously ideal. Poor show chaps. Will try the google code shenanigans instead.

---

### Post by Pott on 2010-03-18
I'm running into issues too. I tried every tricks on this page which didn't involve seamonkey or bloom and still nothing. It asked me to download the Facebook plugin, I put it in the plugins folder (yes I use Firefox 3.6), the user string is already set to 3.6 and I've already installed the IcedTea and JaveSE6 plugins, yet it still won't let me use the uploader. I was prompted for the plugin, installed it, still got prompted, installed it, and now it's AGAIN prompting me for those two plugins, which it then tells me that they're already installed... but nothing.

---

### Post by jalirious on 2010-03-19
Ok, everything else failed - but there is a quick and easy way to upload photos to facebook using fspot.

Install F-Spot

Open F-Spot (Applications > Graphics > F-Spot Photo Manager)

Edit > Manage Extensions > Export (click on arrow to open menu) > Facebook Export > Enable (from right side) > Close

Selecting Images to Export to Facebook

Import (green plus sign) > Select Folder > Open
Select Images for export to Facebook
Photo > Export to > Facebook (This opens a new window)
Login > Opens browser for Facebook permission > Allow > Close
Close Windows “Waiting for Authentication”

Create New Album or Use Existing Album
Add Name, Location or Description (not required)
Add Caption (not required)
Add “In This Photo” (not required)

Add

Done

---

### Post by danopia on 2010-04-28
Ignore this post, I replied to the wrong topic.

---

### Post by myth01 on 2010-05-01
After a clean install of 10.04, I had to sort this out again, Firefox was easy to get up and running (symlink the OpenJDK/IcedTea plugin in /usr/lib/mozilla/plugins), but Chrome still wouldn't play the game.  Tried F-spot and it worked like a charm so will start using that now...

---

### Post by kriti.mysty on 2010-06-27
hello to everyone
ive been having the same problem and just joined ubuntu forums..

BLOOM worked just fine for me..
the simple uploader is too much of  atest to patince for me to upload 50+ pics..

hope this helps

---

### Post by myth01 on 2011-01-03
Chrome continues to work to this day, whether its thanks to or in despite of the many changes facebook has made to the upload process I'm not sure.

The only problem I (she) gets now is a message from Chrome about a page being unresponsive when the file browser is open.  Oh and for some reason selecting any more than about 10 images in the file browser won't work.

Solved.  For now....

---

