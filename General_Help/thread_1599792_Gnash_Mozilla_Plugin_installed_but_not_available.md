---
title: "Gnash Mozilla Plugin installed but not available?"
date: 2010-10-18
forum: General Help
---

### Post by BrokeMahPC on 2010-10-18
I was interested in trying out Gnash as an alternative to Adobe flash Player so I installed it using synaptic and also ticked the Gnash Mozilla Plugin.

Well the plugin is not installed in Firefox? Not there under Tools -Add ons or listed under about: plugins? I tried editing Firefox preferences to use gnash instead of Flash but cant locate the program.

Nothing on the internet as far as basic intructions?

A system search does finds:
/usr/share/app/install/icons/gnash.xpm
/usr/share/app/install/desktop/gnash.desktop

---

### Post by ankspo71 on 2010-10-18
Hi,
I see you installed the Gnash Mozilla Plugin. In my 'apt-cache search' results for gnash, it says:
> mozilla-plugin-gnash - dummy package for renaming to browser-plugin-gnash. 
APT also says that browser-plugin-gnash is a dependency of it, so maybe it didn't do what it was supposed to do by installing browser-plugin-gnash? Try installing browser-plugin-gnash to see if that helps. 

Here is someone that reviewed Gnash recently:
[http://www.thevarguy.com/2010/09/15/testing-gnash-0-8-8-on-ubuntu/](http://www.thevarguy.com/2010/09/15/testing-gnash-0-8-8-on-ubuntu/)
They say it has improved but still has some issues.

If you don't mind me asking, are you trying it out because of performance problems with adobe-flash, or are you trying it because it is open-source? 

I ask because I am trying out a preview release of adobe flash plugin (which is not open-source) and I think it is performing a little better for me that the latest stable version of Adobe Flash. I have only been using it 2-3 days so far though, but so far so good. I'm using Firefox 4 (beta6) + Adobe/Shockwave Flash 10.2.161  (aka "Square" preview release) (32bit)

Here is where you can try it:
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
They have 32bit and 64bit Linux versions available. 


I installed it by extracting the archive first, then copying the plugin to the '/usr/lib/mozilla/plugins' directory. You might want to save your original flash plugin (if any) as a backup somewhere so you can easily reinstall it later.

Hope this helps.

---

### Post by BrokeMahPC on 2010-10-18
I don't have the 'browser-plugin-gnash' in my repositories? There is Gnash, gnash-mozilla-plugin and several other libraries and tools.

Thank you for the info. I wanted to give Gnash a try because it's open source and I would prefer to use open source where possible.

The other reason is I thought I was having a flash problem crashing Xorg (Flash conflict with GPU apparently) but I managed to fix that with some info on a Firefox tweak page.
There have  been many problems with Firefox, Flash and particularly the NoScript extension since 10.04.

This has solved the problem so far.
see here:
[http://ubuntuforums.org/showthread.php?t=1599806](http://ubuntuforums.org/showthread.php?t=1599806)

It looks like Gnash is something for the future and I will stick with Flash for the time being now it is working again. Thank you for your reply tho.

---

### Post by ankspo71 on 2010-10-18
Hi Again,
I did a little digging, and I found out that 'mozilla-plugin-gnash' is being renamed to 'browser-plugin-gnash' in Ubuntu 10.10, the version I am using now. This would be why I see the description of mozilla-plugin-gnash in Ubuntu 10.10 now saying: "dummy package for renaming to browser-plugin-gnash".

I'm glad to hear your computer is doing better now.
> You said:
"Sometimes it would freeze and I had to minimise and maximize the window to get it working again." That part of the problem you were having is the same problem I currently have in Ubuntu 10.10 with Firefox 3.6.10. My display hasn't crashed though. I mentioned that in my blog rant here: [_Sticky Bones_]("http://sticky-bones.blogspot.com/2010/10/bugs-bugs-bugs-ubuntu-1010.html"). I'll try what you said in your other post in the morning and see if the problem goes away. thanks.

---

### Post by BrokeMahPC on 2010-10-21
I had a look in /usr/bin and there is a gnash bash script there titled:
gnash:  Wrapper script for running the different GUI versions of gnash

It ends:
echo "Could not find any <gui>-gnash executable under directory ${THIS_DIR}, with <gui> in $GUI_DIR." >&2
exit 1

Not sure what happened with the install from synaptic?

---

