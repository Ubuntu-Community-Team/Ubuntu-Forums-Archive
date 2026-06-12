---
title: "Can't Embed Video on My Webpage"
date: 2011-07-22
forum: General Help
---

### Post by GrantStoner on 2011-07-22
I apologize - wasn't sure where I should post this - you can move as necessary. Anyways, I'm trying to embed a video on my website, and It keeps asking me if I want to save it, instead of just playing it. How do I embed to play and not pop-up the "save" dialog?```
Today I demonstrated a simple SSH dictionary attack for a friend. Lucky for you - I also recorded it.
(I've made my pw ridiculous and re-secured the box so don't even try it now lol - it'll take 100's of years to crack brute-force).
Anyways, here's what you'll need:<ol><li><a href="http://nmap.org/" target="_blank">NMap</a></li>
<li><a href="http://www.foofus.net/~jmk/medusa/medusa.html" target="_blank">Medusa</a></li>
<li><a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/" target="_blank">PuTTY</a></li></ol>
I also created a password list with 5 passwords (the last one being the correct one) and placed it in my home directory.
<center><iframe width="560" height="349" src="videos/medusa-ssh.avi"></iframe></center>
```That's what I have. It shows the box where the video should be - but doesn't play it, just asks to save. Not sure if it's something with my browser plugins... or my code on my page... ? Tried with FireFox and Rekonq - same results. Tried with many different embed codes as well - all same results. Anyways, any help appreciated.

---

### Post by bodhi.zazen on 2011-07-22
Are you running a web server ? If so, which one ? Apache ? lightttp ? nginx ? 

If so, you need to add avi to your mime types. Should be there by default in apache.

Or are you viewing the file directly ( file:///home/you/web_page.html )?

---

