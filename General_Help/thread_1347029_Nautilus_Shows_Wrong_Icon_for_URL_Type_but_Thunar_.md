---
title: "Nautilus Shows Wrong Icon for URL Type but Thunar Doesn't - How to Fix?"
date: 2009-12-05
forum: General Help
---

### Post by OzzyFrank on 2009-12-05
Hi. I've followed this guide [http://ubuntuforums.org/showthread.php?p=3311005#post3311005](http://ubuntuforums.org/showthread.php?p=3311005#post3311005) for getting **.url **shortcuts from Internet Explorer to open in Firefox in Ubuntu. Since the thread is pretty old, I've had to iron out a couple of issues, but it works fine now. Only thing that doesn't - and is mentioned by another near the end of that thread - is that the icon I specified for the .url type does not show, but .url files show a generic text icon instead.

I've tried obvious things like rebooting, and not so obvious like refreshing the system icon cache, but the icon does not show in Nautilus. However, open Thunar and it shows it fine, so this is obviously a shortcoming of Nautilus.

So, in brief, the steps I took were to create a script, create a symlink to it in /usr/bin called *[COLOR="#0000ff"]Web Shortcut Browser[/COLOR]*, use **assoGiate** to create the .url mimetype, ***Properties > Open With*** to get .url files to open with *[COLOR="#0000ff"]Web Shortcut Browser[/COLOR]* (and made that the default action), and finally in Nautilus I set ***Edit > Preferences > Behaviour > "Executable Text Files"*** to *[COLOR="Blue"]"View executable text files when they are opened".[/COLOR]*

While this is far from being anything major, I'd still like some help, just so I understand what is going on, and know how to remedy it. After all, other file managers show the icon I specified, yet the default program can't, so this is probably bound to happen again with another file-type (though I created a few mimetypes of my own, and all show the icon I picked in Nautilus). I did try changing the icon for the symlink, and even the actual script itself, but it didn't do anything.

---

