---
title: "&quot;bringtofront &lt;window&gt;&quot; command/script"
date: 2009-08-20
forum: General Help
---

### Post by Drostin77 on 2009-08-20
Hello ubuntu world!  Hisashiburi! (Long time no ... post?)

I'm wondering if there is a command to bring a given window to the front... I realize this might be tricky as it might have to interact w/ gnome's desktop environment some component thereof or something, but does anyone know a way to do that with simple command line / a bash script / some scripting language?

I have an HTPC running ubuntu, trying to map a key in my lircrc so that a button on the remote brings mythtv to the front (I have a bad habit of coding on my htpc and forgetting to bring mythtv back...).

P.S.

I got this far:
xwininfo -name "MythTV Frontend" | grep "Window id" | awk '{print $4}' | xargs xdotool windowfocus


which focuses the window but somehow its still in the background...

[EDIT]

Forgot to mention:  xdotool windowraise seems like it should work from the man page, but at least when I try it nothing happens.

[EDIT 2] 

OK, looks like I was too tired last night when I was trying to get this to work, now that I'm properly awake I scrolled past "window" section of the man page onto desktop and window section... anyway if anyone's wondering:


xwininfo -name "MythTV Frontend" | grep "Window id" | awk '{print $4}' | xargs xdotool windowactivate

Will focus mythtv, or anything else if u replace the name bit

---

