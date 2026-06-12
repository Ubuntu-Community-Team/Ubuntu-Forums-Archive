---
title: "OpenCL &amp; &quot;checking for - no&quot;"
date: 2011-04-07
forum: General Help
---

### Post by Julian Luna on 2011-04-07
Hello people. I'm on the "./configure" step to install wine-1.3.17 from the source and I wonder, is it a big problem when terminal shows something like the following?: 

checking for symlink... yes
checking for tcgetattr... yes[COLOR=Red]
checking for thr_kill2... no[/COLOR]
checking for timegm... yes
checking for usleep... yes

I would like to have it perfect and have everything that terminal's looking for like "checking for... - yes". At the end of the diagnose it told me: 

[I]configure: OpenCL 32-bit development files [COLOR=Red]not found[/COLOR], OpenCL won't be supported.

configure: Finished.  Do 'make' to compile Wine.

[/I]But I don't wanna keep going if I don't have the OpenCL 32-bit development files. I googled it but found really large processes related to and I don't know if those are what I'm exactly looking for, so has anyone any idea how can I get those godam 32-bit development files easly? Or I don't care if it's hard but I just want to get them, and the files that terminal's searching for (*Checking for blabla... no*) Thanks people

---

### Post by Julian Luna on 2011-04-08
bump :(

---

### Post by crypto2600 on 2011-04-22
You can get the Ubuntu OpenCL latest (runtime + dev) here:
[http://forums.amd.com/devforum/messageview.cfm?catid=390&threadid=125792&enterthread=y]("http://forums.amd.com/devforum/messageview.cfm?catid=390&threadid=125792&enterthread=y") (Note, get them from the FIRST post - it's been updated recently (April 7) packages **amd_app** and **amd_app-dev**.

After installing, run ./configure again

As for the whole list that gets displayed before with '*yes/no*' the OpenCL warning. Your system doesn't NEED all of them. If you are missing a critical component and there is no substitute for it, it will output an error and you won't be able to run '**make**'

---

