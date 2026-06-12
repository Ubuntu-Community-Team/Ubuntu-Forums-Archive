---
title: "gthumbs missing features in ubuntu 10.10"
date: 2010-12-02
forum: General Help
---

### Post by AgentZ86 on 2010-12-02
Hi

What happened to gthumbs in 10.10
I'm using ubuntu 10.10 64bit

I can't rename files
I can't create photo albums anymore.

Those features are not available now.

Can I get them back?
Or What other application will do this for me NOW ?

Please advise
Thanks

---

### Post by jmszr on 2010-12-02
Agent386,

First, here is the ppa for gThumb 2.12.1: [https://launchpad.net/~webupd8team/+archive/gthumb/+packages](https://launchpad.net/~webupd8team/+archive/gthumb/+packages) , also, here is a link to a Community Cafe thread about Maverick/gThumb: [http://ubuntuforums.org/showthread.php?t=1593689](http://ubuntuforums.org/showthread.php?t=1593689) that I think will be of help to you.

---

### Post by philinux on 2010-12-02
> **AgentZ86 said:**
> Hi

What happened to gthumbs in 10.10
I'm using ubuntu 10.10 64bit

I can't rename files
I can't create photo albums anymore.

Those features are not available now.

Can I get them back?
Or What other application will do this for me NOW ?

Please advise
Thanks

Click on an image thumbnail in gthumb. Edit>rename

---

### Post by mjc1 on 2010-12-03
> **AgentZ86 said:**
> Those features are not available now.

If you are using gThumb 2.12.x, make sure all extensions are enabled in Edit>Extensions. There is a bug that disables them by default under some conditions. The bug will be fixed in 2.12.2.

- Mike

---

### Post by AgentZ86 on 2010-12-04
Ahhh
Thanks

I see gthumbs that ships with maverick is broken
I don't have some of these enable feature to enable them.
So my renaming and web album creator is gone.

I'll get the latest fixes and updates from the repository at gthumbs
Thanks

I'll post back once I see if that fixes things.

Should I remove the old version first then add repos then upgrade

How can I do this manually, without apt get can I just add the repos in the software center ?

---

### Post by AgentZ86 on 2010-12-04
Ok
installed with these instructions the required updates to fix the bugs and missing features.
To version 2.12.1

[http://www.webupd8.org/2010/09/gthumb-2120-stable-has-been-released.html](http://www.webupd8.org/2010/09/gthumb-2120-stable-has-been-released.html)

Still no features
-no right click and rename files
-no create web index or photo albums
-no cropping tool

edit and enable everything but those features are not there to enable them.

Not sure what to do, it's my favorite application I use it everyday to list items on my server for my ebay images and ebay photo album.

Please advise if you have heard anything else and I'll keep searching
Thanks for the replies

---

### Post by AgentZ86 on 2010-12-04
Ok 

The new version has F2 to open the editor, then all the extra clicking to crop images sort of stinks, but I can live with that.
And I found the renaming feature which is stupid, you can't just select them all and right click and rename as before.
I can deal with that too.

Web album tool ?
Move to (tool)

Can anyone explain how to use this ?
The help menu does not mention anything about the web album tool or web indexing tool


Please advise
Thanks for the help

---

### Post by AgentZ86 on 2010-12-06
No create web album feature
No Move to feature

It's practically useless now.

Oh well, anyone have a solution that will create web albums ,crop and rename files similar to the old version of gthumbs ?

Please advise

---

### Post by mjc1 on 2010-12-09
> **AgentZ86 said:**
> No create web album feature
No Move to feature

It's practically useless now.

Oh well, anyone have a solution that will create web albums ,crop and rename files similar to the old version of gthumbs ?

Please advise

Web albums are included in 2.12.1, but the third-party ppa may have been packaged without support for it. I'm not familiar with ubuntu packaging, so I can't help you there. The bison and flex packages need to be present to have web album support. (Read the configure.ac file for web album support tests).

F2 renames files. Simple.

To edit files, press "e" and use the edit tools.

The old-style file copy/move dialog is gone in 2.12.1 - the developer's intent was that you'd use cut and paste (Ctrl+X, navigate with folder tree, Ctrl+V).

However, a file/move tool has been added back into to git master. It's not in a released version yet.

- Mike

---

### Post by mjc1 on 2010-12-09
FYI, I have asked the debian gthumb packager to add the correct bison and flex dependencies to the deb package. Eventually, this correction should make its way into the Ubuntu packages.

- Mike

---

### Post by mjc1 on 2010-12-10
A new ppa has been released (2.12.1-3~webupd8, [https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)) which should fix the web album issue.

- Mike

---

### Post by AgentZ86 on 2010-12-12
Thanks to everyone for the answers

At least someone is aware of it and hopefully that full features will be back soon.

I did see with the last updates of 2.12.1 that there is a Web Album Feature now

Not as complete as the previous as far as setting up themes for the album.
And the move feature is not there, hopefully that will be fixed.

It was such a complete image management tool before and simple to use I really hope it gets solved.

For now I don't have a real solution for my ebay listings anymore except to use the computer in the warehouse with an older version Ubuntu and gthumb on it.

Fingers crossed
:popcorn:

---

### Post by AgentZ86 on 2010-12-12
> **mjc1 said:**
> A new ppa has been released (2.12.1-3~webupd8, [https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)) which should fix the web album issue.

- Mike

If I add this to my Ubuntu sources:
[http://ppa.launchpad.net/webupd8team/gthumb/ubuntu](http://ppa.launchpad.net/webupd8team/gthumb/ubuntu)

Shouldn't it automatically update to the latest version of gthumbs ? 

It's still only updated to 2.12.1

Do I need to tick off Maverick Purposed updates or something ?

The package list only shows the 2.12.1 version currently when following the instruction to add the source as directed at this link.

I already have this source added from the previous instruction

Thanks to everyone for the help and direction

---

### Post by AgentZ86 on 2010-12-12
I'm sorry everyone

I misunderstood the 2.12.1-3

I was thinking 2.12.3 not -3

I see the source is loading the -3 version now so let me investigate the features again to see what I have

Thanks to all

---

### Post by AgentZ86 on 2010-12-12
Ok this is great news thanks to everyone

-The web album feature is working with themes Whooo Hooo !
-The rename feature is shown at the edit tab, but only on a selected folder for some reason.Catalogues do not allow the rename feature for some reason
-The (move) feature is still not there but I can work around that for now, but getting closure
-And the edit file or hitting (e) does not do anything when a folder is selected, only when a catalogue is selected can you access the edit feature

Sort of makes it hard to edit, cause you have edit the files in a catalogue, then move them to a folder to rename them what a pain
I can work with it for now though
I hope the get this worked out

Whew ! I was worried.

---

### Post by bummm on 2010-12-22
According to the way I use gThumb, missing the image preview pane is really bad.
Hope they bring it back.
In the mean time, does anyone know of an alternative WITH an image preview pane??
I'd switch instantly

---

### Post by AgentZ86 on 2011-02-08
gthumbs totally stinks now

---

### Post by AgentZ86 on 2011-02-16
Since there are not other programs that will do all the thing gthumbs use to do I keep playing with it.

I noticed additional misfunction with this program also.

When you have your folder/explore pane open and viewing your files which you may want to move to a folder or create a folder to put them in.

Gthumbs has no ability at all to create or move files.
Well if you could create a folder you might be able to move files that way, but the create folder feature that is greyed out and non functional in gthumbs now too.

I cannot say enough that this program is not useless and it's very annoying that a once superior program is non functional.

I know I keep going on about this but I really liked it.

---

### Post by Sylchat on 2011-03-09
What were they thinking??? I just migrated to 10.10 and I can't crop the image anymore, ALT+C was so usefull... (Using 2.11.3)

edit: oh yeah, found it in the upper right button, I can crop, but it's so slowwwwwww :/

---

### Post by handy on 2011-03-09
Have you guys complained/posted these problems as bugs?

---

### Post by AgentZ86 on 2011-05-17
Oh Thank God it's all fixed up now

A little different to get use to but for those who don't know

[LIST]
[*]-Select your images and right click as before to get the (move to) feature is now working great again
[*]-Select images and Hit F2 To bring up the rename files screen
[*]-Cropping is simple now just double click the file and the paged comes up and all the files in that folder are ready for editing. FYI once you are in that screen there is a (paint edit) icon in the upper right corner.Use this to bring up your crop features.Once you do that select crop, then do your cropping. Once complete just select your picture or the next picture what ever you prever; and then save screen comes up automatically click save. Now your ready to crop you next image just click crop again,when done select next image,click save and so on.
[*]-Saving to web album is actually called Share now. Select (view the folder) icon in the upper left corner this will take you back to your working folder, then you can ctl+a to select all, then click share/web album
[/LIST]

WHEW I thought I would never have another solution that worked so well.

I'm happy again, and all my friends started coming around again LOL

Thanks Ubuntu and Gthumbs

---

