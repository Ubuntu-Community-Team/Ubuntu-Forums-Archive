---
title: "google chrome flash &quot;exe&quot;"
date: 2010-02-02
forum: General Help
---

### Post by leeds_shrew on 2010-02-02
Hi all...

I'm having an issue with a process called 'exe' which seems to control the flash player in Google Chrome.  It EATS my memory, and if I have it open for any extended period of time (which I do - no need to be ashamed... FarmVille...) maxes out my memory, swiftly followed by my swap.  Once this happens it is too late and I am unable to do anything save force my computer off and restart it.

Let's be honest here - I currently have FarmVille running (it's my wife's fault - we're in competition) but I have not done anything. I have only just restarted my computer.  My memory use is 563.3MiB of 874.7MiB - that's 64.4%. Swap is still on the ground.  If I did anything in FarmVille both of these would swiftly rise. (I'm not going to because I'd like to finish this post!) If I look at my processes - exe (which is essentially doing nothing) is using 185.9MiB of memory and between 65 and 110% of my CPU.

(If I hover over the process this comes up: [/proc/self/exe --type=plugin --plugin-path=/usr/lib/flashplugin-installer/libflashplater.so --lang=en-GB --plugin-data-dir=/home/graham/.config/google-chrome/Default --channel=2150.afc39ab0.2029623702 --enable-crash-reporter=0AE30FB3DD8A11329612649DEF1C18CA,Ubuntu 9.10] if that helps anyone identify it)

I'm about to close FarmVille... ... Within 6 seconds my memory use has dropped to 340.8MiB (39%).

Now the obvious question is this: What can I do about it? (Please don't say use fire/swiftfox or another browser) Is it a bug? Should I report it? Who to? Should I just stop playing this daft game and let my wife win?!

Grateful for any help, as always!

G

---

### Post by Leppie on 2010-02-02
flash in linux is in general a memory hog... i know chrome loads quicker with only a few tabs open (i use ff as i usually start it with at least 15 tabs open and chrome just doesn't like that), but doesn't handle flash very well. ff does a better job (sorry, i know you said you don't want ff).

---

### Post by leeds_shrew on 2010-02-02
Well the thing that confuses me is that Chrome was designed around modern web use - ie. lots of java and flash and video etc.

It does seem to run flash quicker, but at the expense of this killer memory problem. Is there a way to cap it off? To limit the amount of memory it consumes and just let it crash the flash app?

---

### Post by Leppie on 2010-02-02
i haven't found any... and reviews i've read didn't speak of such workarounds either...
as i said, chrome is nice if you only open a few tabs. otherwise ff is much better at handling things.
to be honest, i doubt chrome is all that good as google has not even implemented their own toolbar for the chrome browser yet... makes one wonder, doesn't it? it's kind of saying, "we don't really trust our own product either..."

---

### Post by leeds_shrew on 2010-02-02
This is definitely going off topic... But they're selling it pretty big. Every time you head into youtube or on a google homepage it's advertised if chrome isn't detected.

I really think they're trying to move away from the toolbars like you can get for ff or ie - I personally don't like them because they take up half the screen. I really appreciate Chrome's simplicity and speed.  I think (if you can't already) you'll very soon be able to get some google toolbar style addons such as autofill and that great search option it had where you can click to find any word you'd searched for in any webpage.

Going back to the minimalist thing - I'm seriously thinking of ditching my bookmark bar because the new tab page about covers it. It's doing a great job for me, apart from this flash player issue, obviously!

---

### Post by Leppie on 2010-02-02
> **leeds_shrew said:**
> This is definitely going off topic... But they're selling it pretty big. Every time you head into youtube or on a google homepage it's advertised if chrome isn't detected.
chrome apparently has the same security issues as ff (something to do with the chrome zone i believe).

> **leeds_shrew said:**
> I really think they're trying to move away from the toolbars like you can get for ff or ie - I personally don't like them because they take up half the screen. I really appreciate Chrome's simplicity and speed.  I think (if you can't already) you'll very soon be able to get some google toolbar style addons such as autofill and that great search option it had where you can click to find any word you'd searched for in any webpage.[/qoute]
i love simplicity. however, i'm using the google bookmarks function with some button (so i don't need to have he whole toolbar in sight).

[QUOTE=leeds_shrew;8764156]Going back to the minimalist thing - I'm seriously thinking of ditching my bookmark bar because the new tab page about covers it. It's doing a great job for me, apart from this flash player issue, obviously!
what you could try is setting up virtual box gtk, install a windows image and use that for your "flash needs" ;).
xp in a virtual machine seems to be ok (i set one up today to mess around with).

---

