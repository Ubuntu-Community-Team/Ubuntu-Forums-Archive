---
title: "[GUI enhancement] The Firefox icon"
date: 2006-03-17
forum: General Help
---

### Post by calande on 2006-03-17
Hello, I suggest the devs change the dark blue icon of firefox at the top toolbar of Gnome and put the original Firefox icon instead, with the little fox. Until I clicked this blue icon, I had no clue what was gonna happen :) 

[IMG]http://shots.osdir.com/slideshows/593_or/5.png[/IMG]

Just a suggestion :rolleyes:

---

### Post by RJMacReady on 2006-03-17
Yeah, that blue icon is usually used for the Deer Park beta versions of Firefox. Weird.

---

### Post by Tipo on 2006-03-17
You can change it yourself via the applications menu editor in:

Applications -> System Tools

---

### Post by Luke on 2006-03-17
[http://ubuntuforums.org/showthread.php?t=30133](http://ubuntuforums.org/showthread.php?t=30133)

it's something to do with the licensing of the firefox icon. you're not allowed to use it if you change the firefox code at all. apparently the debian devs tweaked FF a little bit and are therefore not allowed to use the official FF icon.

i can see where they're coming from because if someone totally f's up the FF code and then releases it with the FF icon, it could reflect badly on FF.

---

### Post by tribaal on 2006-03-17
Hum this used to bother me a lot too. Then I crafted my own set of icons from firefox's webpage logo.

Here, let me save you guys 2 minutes with Gimp, I attached the images to this post (several sizes)... ;)

Enjoy =)

- Trib'

PS: I have no clue if distributing theses images is legal (the logo probably has some kind of copyright restrictions). Please be kind enough to PM me before you send the cops to my door if it isn't :p

---

### Post by calande on 2006-03-17
Ok, you've been warned, I just called Arnold Schwarzenegger, and he's on his way to go get you \\:D/ 

Kidding aside, I think the changes made to Firefox could be shown to the MoFo, and accordingly they could accept us using the icon. I guess the changes are just not harmful to Firefox after all. These are general rules to protect the Firefox brandname, but on a case by case basis, things are different :rolleyes:

---

### Post by spaceballl on 2006-03-18
I was just going to make a post about this, but then I thought better of it and searched. Seems like i'm not alone on this issue. If we can't use the official firefox logo, that's fine. But while Ubuntu's new theme looks great, that's one ugly blue blob on the top. We should be able to use a nice, generic web browser icon instead of the blue blob.

(however, i also agree that we should either a) not make changes to the initial code or b) just get special permission to change the icon, but assuming these aren't possible, let's just get a new generic one)

---

### Post by Zeroangel on 2006-03-18
I think for a generic icon we should use gnome-globe.png straight out of the gnome theme. It's much more detailed and shiney than the deerpark icon that we're currently using.

I imagine it would also integrate well with the Tango standard.

---

### Post by deadgobby on 2006-03-18
You can change the Icon very easy by DL Easy Ubuntu.
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)
it is very easy and painless.

---

### Post by escape on 2006-03-18
I think changing whats in /usr/share/pixmaps helps a lot, but still when firefox is loading (before it loads the "good" firefox icon in windowlist) the default is stilll the blue globe. I have searched my damndest but haven't found any blue globe icons elsewhere on my computer, at least not by the firefox or mozilla name. Any ideas on how to change this?

---

### Post by powder on 2006-03-18
/usr/lib/mozilla-firefox/icons

---

### Post by impakt on 2006-04-22
[QUOTE=tribaal]Hum this used to bother me a lot too. Then I crafted my own set of icons from firefox's webpage logo.

Here, let me save you guys 2 minutes with Gimp, I attached the images to this post (several sizes)... ;)

Enjoy =)

- Trib'

PS: I have no clue if distributing theses images is legal (the logo probably has some kind of copyright restrictions). Please be kind enough to PM me before you send the cops to my door if it isn't :p[/QUOTE]


just wondering. I was thinking about doing the same thing. I u sed [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) to update to the latest firefox and i want the normal logo. But i save your logos to my desktop. Right click on the crappy firefox logo and go to properties. But the logo i saved is greyed out. How do you apply it? thanks

---

### Post by aysiu on 2006-04-22
[QUOTE=impakt]just wondering. I was thinking about doing the same thing. I u sed [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) to update to the latest firefox and i want the normal logo. But i save your logos to my desktop. Right click on the crappy firefox logo and go to properties. But the logo i saved is greyed out. How do you apply it? thanks[/QUOTE] I did consider making icon replacement part of the script, but I didn't want to be presumptuous about what people want. All I know, from people using my script, is that they want the newest Firefox.

However, [this script to change the icons](http://ubuntuforums.org/showthread.php?t=34354) has been around for a while and (if you look toward the end of the thread) has been updated for Dapper, too.

---

### Post by impakt on 2006-04-22
[QUOTE=aysiu]I did consider making icon replacement part of the script, but I didn't want to be presumptuous about what people want. All I know, from people using my script, is that they want the newest Firefox.

However, [this script to change the icons](http://ubuntuforums.org/showthread.php?t=34354) has been around for a while and (if you look toward the end of the thread) has been updated for Dapper, too.[/QUOTE]

[QUOTE=tribaal]Hum this used to bother me a lot too. Then I crafted my own set of icons from firefox's webpage logo.

Here, let me save you guys 2 minutes with Gimp, I attached the images to this post (several sizes)... ;)

Enjoy =)

- Trib'

PS: I have no clue if distributing theses images is legal (the logo probably has some kind of copyright restrictions). Please be kind enough to PM me before you send the cops to my door if it isn't :p[/QUOTE]

I tried the script but me being such a newbie at this i couldnt even get past the first line.  Not entirely shure what im doing wrong. 

I enter the first script and it opens up gedit. tried a few different things from here but basically cant go any further. 

all help is appreciated

---

### Post by Ramses de Norre on 2006-04-22
Paste the script (starting with #! /bin/sh) into gedit and save it, then run the following commands.

---

### Post by impakt on 2006-04-22
[QUOTE=Ramses de Norre]Paste the script (starting with #! /bin/sh) into gedit and save it, then run the following commands.[/QUOTE]

did that. This is what i get in terminal

"chris@ubuntu:~$ sudo chmod +x /usr/local/bin/restore_mozilla_icons
chris@ubuntu:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
Replace the Mozilla Firefox document icon (y/n)? [y] y

Do you want to divert the original packaged files to alternate locations
(make the changes permanent) (y/n)? [y] y

Downloading and replacing icons. Please wait..... done !

Shall I reload gnome-panel to apply the changes (y/n)? [y] y "


and nothing changes it reloads all my icons but no change in anything. Thanks

---

### Post by impakt on 2006-04-22
Oh crap. Nevermind it worked. It  still had the old icon in my panel. But the icon in the applications tab changed. So i just removed from panel and reinserted it and it worked. Thanks everyone.

---

