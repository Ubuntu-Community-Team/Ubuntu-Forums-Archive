---
title: "Remapping keys"
date: 2011-08-25
forum: General Help
---

### Post by redaler1 on 2011-08-25
Hello,

I am trying to remap a key to a combination of keys.
Using capslock as a modifier I want to turn jkli into arrow keys and make 'u' move one word left when editing text (produce ctrl+left) whenever capslock is pressed. Without the capslock being pressed jkliu perform as usual.

Moreover, I do not want to block other modifiers. i.e.: capslock+shift+j would produce shift+left
capslock+shift+alt+l would produce shift+alt+l
Only particular keys are remapped (j,k,l,i,u,d...) when capslock is pressed and the effect of all the modifiers (shift, alt, ctrl) is not blocked.

Any suggestions?

---

### Post by kirilp on 2012-01-12
somebody tried it already 

[INDENT][COLOR=Black]http://duartes.org/gustavo/blog/post/home-row-computing/comment-page-1#comment-13209
[/COLOR][COLOR=Black]Paul on 						January 26th, 2009 6:46 pm  			[/COLOR][COLOR=Black]Okay, I got it working on my Linux laptop, if not supremely  elegantly. Evidently there is some overlapping of tasks between xkb and  xmodmap under Xorg, so just setting the settings in xmodmap wasn’t doing  the trick.[/COLOR]
[COLOR=Black]First I made an ~/.Xmodmap file to turn my Caps Lock key into a modifier:
  clear Lock
  keycode 66 = ISO_Level3_Shift[/COLOR]
[COLOR=Black]Then I modified the first stanza of my /usr/share/X11/xkb/symbols/us file  to add the keymappings I wanted:[/COLOR]
[COLOR=Black]    key  {        [         h,    H,      Left     ]       };
    key  {        [         j,    J,      Down     ]       };
    key  {        [         k,    K,      Up       ]       };
    key  {        [         l,    L,      Right    ]       };[/COLOR]
[COLOR=Black]I saved both files and activated the changes with
setxkbmap ; xmodmap ~/.Xmodmap[/COLOR]
[COLOR=Black]And it works great! Thanks for the idea — it’s a real time-saver.[/COLOR]
[COLOR=Black]I don’t think you’d need a kernel module to make it work on the console; I think the built-in loadkeys can handle that.[/COLOR]
[/INDENT] 			       			
but didnt work when I tried it. But I am also interested in something like this

---

