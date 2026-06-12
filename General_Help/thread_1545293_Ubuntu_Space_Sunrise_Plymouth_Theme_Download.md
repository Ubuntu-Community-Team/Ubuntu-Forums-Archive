---
title: "Ubuntu Space Sunrise Plymouth Theme Download"
date: 2010-08-03
forum: General Help
---

### Post by mendhak on 2010-08-03
There's a very cool Plymouth Theme called [space sunrise (watch the video)](http://www.youtube.com/watch?v=qaSg2rRj4HQ&feature=related).  There's even a tutorial on how to install it [here](http://ubuntuforums.org/showthread.php?t=1453733&highlight=space+sunrise), however the actual files required have gone missing from gitorious.org.  Is it alright to post it here for the benefit of others who might be looking for it?

If not, apologies.

---

### Post by subSYStem on 2010-08-05
Thanks a lot, mendhak!

Works like a charm with the "15" setting. Great - wanna see more stuff like that from you...

N1! :D

---

### Post by didooofidooo on 2010-08-14
Thanks so much, this theme was removed from the author's GIT repository and I couldn't get it from anywhere else :D

---

### Post by tijs14tijs on 2010-08-21
Thank you :D I was looking 4 this a while

Great soooo nice

---

### Post by BigSilly on 2010-08-23
Just wanted to say a big thanks for sharing. I have now installed this, and even the missus thought it was brilliant.

Many thanks! :)

---

### Post by coolman98 on 2010-08-23
cool

---

### Post by coolman98 on 2010-08-23
error: test.sh: 9: Syntax error: Bad for loop variable

---

### Post by coolman98 on 2010-08-23
please it is so cool

---

### Post by Freezewarp on 2010-08-25
The author moved his code to:
[http://gitorious.org/oskude/space-sunrise/](http://gitorious.org/oskude/space-sunrise/)

(Found that in a lone Youtube comment after an hour of searching.)

I had no errors compiling it, though depending on how you install it (that is to */lib/plymouth* instead of */usr/share/plymouth*) you will need to change the *space-sunrise.plymouth* file. This may just be bad practice on my part, though.

---

### Post by schreber on 2010-08-25
Looks pretty interesting, thanks for sharing.

---

### Post by jack frost on 2010-08-27
> **mendhak said:**
> There's a very cool Plymouth Theme called [space sunrise (watch the video)]("http://www.youtube.com/watch?v=qaSg2rRj4HQ&feature=related").  There's even a tutorial on how to install it [here]("http://ubuntuforums.org/showthread.php?t=1453733&highlight=space+sunrise"), however the actual files required have gone missing from gitorious.org.  Is it alright to post it here for the benefit of others who might be looking for it?

If not, apologies.

thanks!! i was looking for this.

---

### Post by jack frost on 2010-08-27
> **mendhak said:**
> There's a very cool Plymouth Theme called [space sunrise (watch the video)]("http://www.youtube.com/watch?v=qaSg2rRj4HQ&feature=related").  There's even a tutorial on how to install it [here]("http://ubuntuforums.org/showthread.php?t=1453733&highlight=space+sunrise"), however the actual files required have gone missing from gitorious.org.  Is it alright to post it here for the benefit of others who might be looking for it?

If not, apologies.


If you want to add plymouth boot screens that are in the repos I found this link:

 [http://crashsystems.net/2010/04/changing-plymouth-themes/](http://crashsystems.net/2010/04/changing-plymouth-themes/)

use the command  [SIZE=5][/SIZE][I][SIZE=5][B]apt-cache search plymouth-theme

[/B][/SIZE]-it will list all the plymouth boot screens in the repos.
then just type[SIZE=4]** sudo apt-get install (name of the theme)**[/SIZE]
ubuntu will install in :  libs/plymouth/themes

run this : [/I][SIZE=6]sudo update-alternatives --config default.plymouth

[/SIZE][I]it will make a window pop up and you can choose from what theme you want to install corresponding to the theme name. Each theme will have a number next to it. just type in the number and hit enter.

then type:  [/I][SIZE=6]sudo update-initramfs -u

Reboot and enjoy the new boot theme.[/SIZE]

I like the solar one so far from the repos; but I think the sunrise may have it beat. There is another theme called plymouth-orange 10.4 that is good too.  The ones in the repo's do not did require any manual copying etc. to work.

---

### Post by inameiname on 2010-09-02
Thanks as well. I was also looking for this. It's very cool. Nice customization.

---

### Post by vedix on 2010-09-02
Thanks for the guide.

Is it possible to _disable_ space-sunrise (or any other Plymouth theme) from running at "_shut down_"?  .

---

### Post by chirul on 2010-11-16
thank's lot.......... bro..

---

### Post by inameiname on 2010-11-17
Not sure, but you might be able to tweak the code found in the deb file, below:

[http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678](http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678)

Might just be a simple removal of that part of the configuration, idk.

---

