---
title: "gthumb - how to revert to earlier version."
date: 2010-11-11
forum: General Help
---

### Post by lathanial on 2010-11-11
OS - Ubuntu 10.10

The new version of gthumb (2.12.0) no longer has the web album creator which I used a lot. How can I revert back to version 2.10.11 or earlier? 

Thanks,
lathanial

---

### Post by cucu007 on 2010-11-11
Well let us know if this help>

[http://www.webupd8.org/2010/04/gthumb-211x-removed-from-ubuntu-1004.html](http://www.webupd8.org/2010/04/gthumb-211x-removed-from-ubuntu-1004.html)

---

### Post by mjc1 on 2010-11-12
> **lathanial said:**
> The new version of gthumb (2.12.0) no longer has the web album creator which I used a lot. How can I revert back to version 2.10.11 or earlier?

Not true: 2.12.0 does have a web album creator.

Check that you have "Web Albums" enabled in Edit > Extensions, and then use the Share > Web Albums tool.

- Mike

---

### Post by lathanial on 2010-11-12
Thanks cucu007,

I followed the link but wasn't sure about how to use the information it provided. It did inspire me to research the use of repositories though. I learned how to add the lucid repository to software sources and get an earlier version(2.10.11) of gthumb that does what I need.

Thanks again for the quick reply,
lathanial

---

### Post by lathanial on 2010-11-12
Thanks also to mjc1.

I stand (sit) corrected. gthumb 2.12.0 does have a feature to generate a Picasa Web album. It seems to work good but I can't use it like I did the gthumb web album in the earlier version. With the earlier version I could very quickly resize, rename, and generate a web gallery of equipment photos that I could very easily add to my website in just a few key strokes. The script that gthumb used for generation wasn't documented very well (at least I couldn't find any lit on it) but it was so easy to figure out that even I could add my own styles and graphics to the generation process as well. 

It may be possible to do this in the new version - the scripting and re-use of code - but I couldn't figure it out. Everything else seemed to work very well once I found out where all the tools and options were located. gthumb has always been one of my favorites pieces of sw in linux and I hope they add the functionality that I liked back in although I don't know why they would if I'm the only user to use it that way.

More than you wanted to know I'm sure.

Thanks
lathanial

---

### Post by mjc1 on 2010-11-12
> **lathanial said:**
> I stand (sit) corrected. gthumb 2.12.0 does have a feature to generate a Picasa Web album.

No, no! There is a "Share > Picasa Web Album" function, and a "Share > Web Album" function. They are different. 

The "Share > Web Album" function is what you want. It is quite similar to the old web album function in 2.10.x.

- Mike

---

### Post by lathanial on 2010-11-13
Hi Mike,
I don't have an option to enable "Web Albums" under Edit> Extensions which is probably why I don't have a "Share > Web Album" function. I tried clicking on "More Extensions" but that wasn't helpful. Does the "Web Album" extension come with the package by default or do I have to add it?

Thanks for your help.
lathanial

---

### Post by mjc1 on 2010-11-14
> **lathanial said:**
> Hi Mike,
I don't have an option to enable "Web Albums" under Edit> Extensions which is probably why I don't have a "Share > Web Album" function. I tried clicking on "More Extensions" but that wasn't helpful. Does the "Web Album" extension come with the package by default or do I have to add it?

Thanks for your help.
lathanial

Hmm, weird. 2.12.0 does have the web album by default, although perhaps the Ubuntu package is missing some prerequisites (and thus the extension doesn't compile, and isn't shown). I don't run Ubuntu myself, so I'm can't confirm... I run Fedora 14.

- Mike

---

### Post by lathanial on 2010-11-15
I looked at the source files and the code does appear to be there for "Web ALbums" as well as the album themes and such but it isn't in the package I installed from webupd8 team. Hopefully it will show up soon as the 2.12.0 release (seems odd to have a choice of different 2.12.0 releases) seems to be an improvement. For now I'll keep trucking with 2.10.11.

lathanial

---

### Post by mjc1 on 2010-12-10
A new ppa has been released (2.12.1-3~webupd8, [https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)) which should fix the web album issue.

---

### Post by lathanial on 2010-12-10
Thanks Mike,
I've installed 2.12.1 and enabled web albums and it works fine. Any idea where the new hiding place for the album themes is. They used to be under "~/.gnome2/gthumb/albumthemes".  Also, I assume that I can still create my own themes. Do you know if that is correct?

lathanial

---

### Post by mjc1 on 2010-12-10
/usr/share/gthumb/albumthemes
~/.local/share/gthumb/albumthemes

I believe you can still make your own themes, although I haven't tried.

- Mike

---

### Post by lathanial on 2010-12-10
I found the themes in /usr/share/gthumb/albumthemes but not under ~/.local

It appears that you can make your on themes but it looks like the scripting language has changed. I can't use the themes I created as they are. I never found documentation for the old style script but I guess if no one knows where to find it I can work it out again. In messing around with it I did find that you must have a file "preview.png" in your theme directory to get your theme to show up in the "share->web album" dialog.

It would be a lot more convenient for development if the themes were kept under the home directory and didn't have to use sudo to access the files.

Thanks for your help
lathanial

---

### Post by mjc1 on 2010-12-10
> **lathanial said:**
> I found the themes in /usr/share/gthumb/albumthemes but not under ~/.local

It appears that you can make your on themes but it looks like the scripting language has changed. I can't use the themes I created as they are. I never found documentation for the old style script but I guess if no one knows where to find it I can work it out again. In messing around with it I did find that you must have a file "preview.png" in your theme directory to get your theme to show up in the "share->web album" dialog.

It would be a lot more convenient for development if the themes were kept under the home directory and didn't have to use sudo to access the files.

Thanks for your help
lathanial

The system-wide default themes are kept in a directory that everyone can read (/usr/share/gthumb/albumthemes). 

To make your own theme, copy one of the existing ones to your own private theme folder, ~/.local/share/gthumb/albumthemes, and modify it as required. This folder does not exist by default.

gThumb should look in both folders for themes.

- Mike

---

### Post by lathanial on 2010-12-11
Thanks Mike
It works great.

lathanial

---

### Post by avongil on 2011-03-13
Thanks!  I was getting worried gthumb no longer supported web albums. Awesome software.

---

