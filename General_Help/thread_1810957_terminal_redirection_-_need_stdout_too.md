---
title: "terminal redirection - need stdout too"
date: 2011-07-24
forum: General Help
---

### Post by DanBender on 2011-07-24
I'm trying to run nuvesport on a mythtv installation and am having trouble getting it to output anything but an empty file. The terminal output says "ffmpeg died early" and prompted me to run nuvexport --debug to help diagnose the real error. Anyway, I'm trying to run that option and redirect the output to a file I can parse at my leisure. Unfortunately,```
nuvexport --debug > nuvexport.txt
```sends the output to a file INSTEAD OF the terminal, meaning I don't see any prompts or anything in the terminal. Some of you are now saying "Duh! That's what it's supposed to do!" The problems this causes for me is that nuvexport is an interactive script, and I need to be able to see what it's prompting me for in order to make it actually do something. Is there a better way to run it interactively and then put the output of the script to a file? I believe what nuvexport actually produces is a list of shell commands for other tools to process, and I need to see what it's asking *them* for. I'd like to be able to look at that list of commands and have the ability to stop and look at it later, rather than leaving my terminal open for however long it takes me to get back to it, if that's possible.

(I'm not asking about the problem itself yet because I'd rather wait until I can actually get some information before I just post "I can't get this to work help plz")

Thanks,
-Dan

---

