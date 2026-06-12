---
title: "Dreamweaver Open Source Equivalent?"
date: 2009-08-26
forum: General Help
---

### Post by mapes12 on 2009-08-26
I maintain a couple of hobby websites for which I have one windoze box left to use Dreamweaver to keep the sites up to date etc. I've had a Google around for an open source equivalent but somewhat confused as to the potential applications. Quanta Plus has good reviews but it doesn't appear to have any development work done since 2004.

Any input / suggestions greatly appreciated.

TIA

Mark

---

### Post by dariyoosh on 2009-08-26
> **mapes12 said:**
> I maintain a couple of hobby websites for which I have one windoze box left to use Dreamweaver to keep the sites up to date etc. I've had a Google around for an open source equivalent but somewhat confused as to the potential applications. Quanta Plus has good reviews but it doesn't appear to have any development work done since 2004.

Any input / suggestions greatly appreciated.

TIA

Mark

Personally, I never worked with Dreamweaver, however I know that it is really a great tool and in particular includes many automatic functions. I worked with Quanta Plus, in my point of view, it is a very interesting tool, for someone who is willing to develop himself with HTML, JavaScript, etc. (I mean typing source code). Unless there has been changes in recent years (I used it several years ago) it is far away to have the same functionalities as Dreamweaver.


Regards,
Dariyoosh

---

### Post by 3rdalbum on 2009-08-26
You have to decide what sort of editing program you want.

1. HTML text editor. These show you the HTML and provide functions for working with it (like adding tags, folding tags up so you can temporarily hide the contents, etc). Quanta Plus is an HTML text editor.

2. WYSIWYG (What You See Is What You Get) editors. These show you what the page in its current state will look like in a web browser. You can edit elements on the page just like you would edit a Microsoft Word document, for instance. Dreamweaver is a WYSIWYG editor.

Most people suggest Kompozer or Nvu as good WYSIWYG web editors, but I've run into showstopper issues with these and they are both abandoned projects as far as I can see (Kompozer was forked from Nvu when Nvu's development stopped).

Your two options are:

Seamonkey. It's the successor of Netscape Communicator, and contains a basic WYSIWYG web editor.

Or, find a WYSIWYG program that runs in Wine.

---

### Post by coolmanlg on 2009-08-26
You can run dreamweaver cs3 in wine. It run quite well. Komozer and NVU are no match for dreamweaver. I have tried them in the past and I went back to dreamweaver. I wish they can have native code for Linux.

---

### Post by credobyte on 2009-08-26
Haven't tried by myself, however, have heard a lot about Kompozer ( which *is* very similar to Dreamviewer ).

---

### Post by fela on 2009-08-26
You want to try vim:

```
sudo apt-get install vim
```

You can do all your coding from there :popcorn:

---

### Post by nmccrina on 2009-08-26
> **fela said:**
> You want to try vim:

```
sudo apt-get install vim
```

You can do all your coding from there :popcorn:

Oh gosh! :P

---

### Post by fela on 2009-08-26
> **nmccrina said:**
> Oh gosh! :P

Gvim if you want a GUI. Vim is actually alot more user friendly than things like MS word or openoffice. Think, if you've never used a computer before:

How do I delete? Maybe the letter d....oh no for some reason they put it as ctrl+x!

How do I paste....maybe p? Nah, ctrl+v...I mean what does V have to do with pasting!

---

### Post by credobyte on 2009-08-26
> **fela said:**
> Gvim if you want a GUI. Vim is actually alot more user friendly than things like MS word or openoffice. Think, if you've never used a computer before:

How do I delete? Maybe the letter d....oh no for some reason they put it as ctrl+x!

How do I paste....maybe p? Nah, ctrl+v...I mean what does V have to do with pasting!

:lolflag:

If *p* would mean *paste* and *d* would perform *delete* action, people would reinstall their OS's more often than they do it now.

---

### Post by racerraul on 2009-08-26
I've used older Versions of Dreamweaver in the past.
It is not just a WYSIWYG editor it also support changes to the HTML code as well as previews from browsers all in 1 tool.

---

### Post by andrew.46 on 2009-08-26
Hi mapes12,

> **mapes12 said:**
> I maintain a couple of hobby websites for which I have one windoze box left to use Dreamweaver to keep the sites up to date

Your situation mirrors my own in that I also keep 3 hobby websites going and I am a former Dreamweaver user. In fact I used the version before Adobe took over. I do not believe you will ever find a similar piece of software to Dreamweaver in the linux world and this gives you the choice of a VM, wine or selecting something wih different goals to the all encompassing Dreamweaver. My own solution was to get a little closer to the html and use Bluefish, perhaps you might try this one as well?

Andrew

---

### Post by Old Marcus on 2009-08-26
Kompozer is still being worked on, and has some fairly stable alphas out now, which are more stable than the old one on GTK 2.14 upwards.

---

### Post by akakingess on 2009-08-26
> **coolmanlg said:**
> You can run dreamweaver cs3 in wine. It run quite well. Komozer and NVU are no match for dreamweaver. I have tried them in the past and I went back to dreamweaver. I wish they can have native code for Linux.

I'll be perfectly honest, I dual-boot Ubuntu and Windows 7 just for CS3 and all the tools that come with it. I just do not want to run Wine at all, and as soon as I find something comparable to Dreamweaver that is open source I will say goodbye to Windows for good!

---

### Post by fela on 2009-08-26
Just use vim, or gedit if you absolutely need the 'familiarity'. Familiar if you come from windows, alien if you used vi/emacs all your life. Code HTML with that rather than letting some automated program generate obfuscated HTML by itself. It's much better in the long run doing it yourself.

> If *p* would mean *paste* and *d* would perform *delete* action, people would reinstall their OS's more often than they do it now.

Why? I completely fail to see your point here, sorry.

---

### Post by GoldenSun on 2009-08-26
just ssh into website and use nano for real-time editing.  
I used ms sharepoint because was free before I used straight html.
It was ok, but programs like that make the code messy and hard to interpret sometimes.

---

### Post by Thelasko on 2009-08-26
I posted [a poll]("http://ubuntuforums.org/showthread.php?t=1086769&highlight=Dreamweaver") on this topic a while ago.

---

### Post by darksideforge on 2009-08-26
> **Old Marcus said:**
> Kompozer is still being worked on, and has some fairly stable alphas out now, which are more stable than the old one on GTK 2.14 upwards.

Just an update to this: according to the website: [http://kazhack.org/?post/2009/05/14/KompoZer-0.8a4]("http://kazhack.org/?post/2009/05/14/KompoZer-0.8a4") there are known issues using any Ubuntu OS post-7.04 with Kompozer where GTK 2.14 or greater is used. The alpha4 release of Kompozer is out and is addressing this (as of 14 May 2009). Using a version of Komposer 0.7 with 9.04 is supposed to yield good results but I haven't tried it yet...maybe later tonight.

As far as SeaMonkey Composer goes, my own experience is that it is absolutely great when used for composing simple, static HTML sites/pages. Functionality of drop-down menus and CSS templates is non-existent. There are also issues with background colors and font changes...especially if editing an existing site (not quite so noticeable when starting from scratch).  Source and Anchors show up very well, but folding anchors present occasional problems. In a rare event, SMC will import and style tables very well for you, but FORGET trying to edit the table after you've imported it/them...you're better off starting all over from scratch. Oh, and as far as importing a site created with Joomla or Drupal, you'll have better success jumping off a bridge. Make sure there are rocks at the bottom because you DO NOT want to live through the experience more than once! WYSIWYG is *_very_* limited when it comes to importing/using/saving image files as well.

As a last note, and I'm surprised nobody has mentioned this yet, if you have the memory available on your HDD you may want to consider using Synaptic to install a MySQL database and then also installing the Drupal6 CMS. I've found that Drupal6 is more difficult to learn but yields superior results to Joomla 1.5 (although Kudos to the Joomla folks for making the learning curve short & sweet). I installed both Drupal6 and Joomla 1.5 to my limited Toshiba Satellite laptop and also installed them to my server. Transferring files back and forth between the two hasn't been an issue as of yet (although admittedly I'm in my infancy with both programs).

And, since I brought up those two, you MAY want to consider downloading and installing WordPress for your two static web pages. It may be a little bit of time involved transferring data over to a WordPress page, but the result is worth it. If you aren't aware, there are many free WP themes out there and it isn't just for blogging anymore...I've recently run across some WP "page" themes (as opposed to the standard Blog themes) and they look really nice. They do well with PHP and CSS/HTML/XHTML...about the only thing I haven't seen with a WP theme/page is drop-down menus.

I hope this long-winded diatribe has helped. If you need some links for any of this stuff, I've got hundreds stored in .html format from my Bookmarks backup files. Let me know.

---

### Post by jerome1232 on 2009-08-26
Is [Aptana]("http://aptana.com/") any good? Looks like it's an eclipse module, can import dreamweaver stuff and etc...

I don't do web development but it looks good to me, can't give a qualified opinion.

---

### Post by akakingess on 2009-08-26
Aptana looks to concentrate on actual web applications, and not necessarily on web site development. I could be mistaken cuz i just took a quick look, but doesn't mean it's not bad at what it does, just don't think that it does site development. Keep the input coming, though, we need all the eyes and ears we can get, like I stated earlier, I am just waiting for an open-source alternative to CS3 and then I can finally say GOODBYE WINDOWS!!!!

---

### Post by R_W322 on 2009-08-27
Try downloading BlueFish from the Repos.

RYAN.WDZIECZNY

---

### Post by darksideforge on 2009-08-27
> **akakingess said:**
> Aptana looks to concentrate on actual web applications, and not necessarily on web site development. I could be mistaken cuz i just took a quick look, but doesn't mean it's not bad at what it does, just don't think that it does site development. Keep the input coming, though, we need all the eyes and ears we can get, like I stated earlier, I am just waiting for an open-source alternative to CS3 and then I can finally say GOODBYE WINDOWS!!!!

According to the website, it does everything:
> 
[COLOR="Red"]Unified Editing for Web Apps

Aptana Studio's editors provide world-class HTML, CSS, and JavaScript code completion, reference, and validation at your fingertips.
	Ajax and JavaScript Libraries

Get unrivaled support for popular libraries including jQuery, Prototype, YUI, dojo, Ext JS, MooTools, and others.
PHP, Ruby on Rails and Python

Add powerful plugins and ready-to-use runtimes for PHP, Ruby on Rails, and Python. Add Studio to Eclipse for Java.
	Desktop Ajax

Use your skills to create desktop web applications with our plugin for Adobe AIR.
Free, Open Source and Cross Platform

Download Aptana Studio for Windows, Mac, or Linux. Both the standalone and Eclipse plugin distributions are free, open source software.
	Yeah, it's in there.

Multi-browser previews, SQL database tools, an awesome JavaScript debugger, server tail views, and tons more.[/COLOR]

It isn't free/opensource, but it says it's fully Linux compat, so maybe we're making headway after all.

---

### Post by jerome1232 on 2009-08-27
In your quote it says the standalone and the eclipse plugin versions of Aptana are Free, Open Source Software.

> Aptana Studio is free, open source software. 

edit: But then again I can't find where you can obtain the source code. They also have a 'pro'version for $100. So now I'm confused.

2nd edit: awww, found where you can get the source and the pro version comes with support and early access to new builds.

---

### Post by akakingess on 2009-09-13
> **darksideforge said:**
> According to the website, it does everything:


It isn't free/opensource, but it says it's fully Linux compat, so maybe we're making headway after all.

Again, I see a whole lot of "Apps Development" but not necessarily design. Maybe it's just me but I see a difference, sure we definitely use plenty of apps on our sites nowadays, but that does not mean that it can 'design' the site. I hope I am wrong and will give it a shot over my weeekend Sun/Mon/Tues and see what all the software entails.

---

### Post by darksideforge on 2009-10-06
> **mapes12 said:**
> I maintain a couple of hobby websites for which I have one windoze box left to use Dreamweaver to keep the sites up to date etc. I've had a Google around for an open source equivalent but somewhat confused as to the potential applications. Quanta Plus has good reviews but it doesn't appear to have any development work done since 2004.

Any input / suggestions greatly appreciated.

TIA

Mark

I've had mixed results with Seamonkey Composer, terrible results with Kompozer, and am still experimenting with Amaya. What I'm really enjoying learning with is both gedit and Aptana. While these last two are not WYSIWYG editors, I've had great results with editing the actual code in both gedit and Aptana, and then pulling up the edited site file in Firefox...and then refreshing after every change so that I can check my progress.  Between that and some online tutorials I've found for html and xml, I feel like I'm doing pretty well with it to have only been doing it for a little over a month and being completely self-taught (well, with this forum I suppose it's not exactly correct to say totally SELF-taught, but close enough.  ;-)

---

### Post by DracoJesi on 2009-10-06
I'm also a former Dreamweaver user, I was (and am) extremely disappointed that an Operating system that has been seen as "the OS for coders" in the past, lacked anything like Dreamweaver.....

the best I've found is Bluefish, I love how it is geared toward many different programming languages, but it lacks certain features.......

Kompozer has plug-in issues as far as I know, I couldn't find many for it and was told it's because they were implemented so badly you might as well not use them.....

never heard of Vim, I'll have to try it....

I think I tried seamonkey,if it's the one I'm thinking of.....it's very simplistic, but then all you really need to code is a text editor most of the time lol

---

### Post by dannyboy79 on 2011-03-11
has anything changed in this area as far as an open source equiv to dreamweaver? I know this is an old post but very curious about this? Basically what I am looking for is a place to add a website so I can edit colors and formatting in real time to see my changes. Im a complete noob to web design and don't know the first thing but someone told me to check out dreamweaver but I am an UBUNTU user till the end.

It's just for a hobby website/forum which is currently installed on my home server. It's SMF (simple machines forums) version 1.1.11 installed on 10.04. I don't know HTML or any langauge. Any help would be appreciated.

---

### Post by graphius on 2011-04-18
I used to use Dreamweaver years ago, but I found that after I started to understand HTML (with the help of a couple of books and a bit of Internet research) I ended up hand editing all of Dreamweavers pages in notepad (yes this was before I saw the light..:)  )
Now I tend to use CMS like [wordpress]("http://wordpress.org/") or [gallery2]("http://gallery.menalto.com/") (I am into photography) and tweak the design with Bluefish.

---

### Post by fela on 2011-04-18
I don't see what's wrong with a bog standard text editor (as long as it does line numbering and syntax highlighting).

And obviously, tabbed editing, session remembrance, and a few other gubbins :P

---

### Post by danieee on 2011-06-01
i still prefer dreamweaver, it just makes the job easy...I need something like it for my ubuntu 11.04..any ideas?

---

