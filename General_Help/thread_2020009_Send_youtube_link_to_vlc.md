---
title: "Send youtube link to vlc"
date: 2012-07-07
forum: General Help
---

### Post by evilsoup on 2012-07-07
OK so what I want to do is add an option to the firefox context (right-click) menu, so that when I right-click on a youtube link I have the option to send it to VLC.

Currently I use 'copy link location' and then use a key combination to activate a tiny script

```
#!/bin/bash
foo=`xclip -o -selection clipboard`
vlc "$foo"
exit 0
```

but it would be much easier if I could just right click and take out a step.

I would also like to add the same option to the context menu when right-clicking a youtube video (mostly for embedded videos); this is less important, but I figure it would be pretty trivial if I get the other thing working.

So. Does anyone know of an add-on or extension or whatever that will let me do this?

---

### Post by ajgreeny on 2012-07-07
What you want sounds rather like the flash video-replacer add-on for firefox.
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/developers](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/developers)

---

### Post by evilsoup on 2012-07-07
That looks pretty cool, and I'll probably test it out, but it isn't what I'm looking for.

On some forums I go to, people post a lot of youtube videos in threads about music. Queuing these up in VLC and leaving them to play in order would be quite handy. This also happens over google talk. That's the sort of reason I want this context-menu option.

---

