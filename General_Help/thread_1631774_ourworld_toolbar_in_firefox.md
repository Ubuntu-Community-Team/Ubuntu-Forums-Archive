---
title: "ourworld toolbar in firefox"
date: 2010-11-27
forum: General Help
---

### Post by jeremybentham on 2010-11-27
My daughter managed to install this annoying add-on to firefox. I uninstalled it in the firefox tools menu but the logo is still there every time I use firefox. How can I get rid of this?

---

### Post by SpotHT on 2010-11-27
[COLOR=red][COLOR=Black]Open the terminal and issue this command to run Firefox in safe mode:[/COLOR][/COLOR][B][COLOR=red]

             [/COLOR][/B]```
**[COLOR=red]/path/to/firefox -safe-mode[/COLOR]**
```[B][COLOR=red] 

[/COLOR][/B][COLOR=red][COLOR=Black]In the window that appears, [/COLOR][/COLOR][COLOR=Black]check on[/COLOR]** Reset toolbars and controls**, then hit **Make Changes and Restart**.

---

### Post by jeremybentham on 2010-11-27
thanks but,

tad@tad-SB61V40:~$ /path/to/firefox/firefox -safe-mode
bash: /path/to/firefox/firefox: No such file or directory
tad@tad-SB61V40:~$ 

Maybe I've missed a command that you thought was obvious as I am not a terminal user

---

### Post by jeremybentham on 2010-11-27
By the way, I even uninstalled firefox and then reinstalled it and the ourworld thing was still there

---

### Post by SpotHT on 2010-11-29
run instead this command:

```
**/usr/bin/firefox -safe-mode**[B][B][COLOR=red]
[/COLOR][/B][/B]
```[B][B][COLOR=red]
[/COLOR][/B][/B]

---

### Post by jeremybentham on 2010-12-12
Thanks Spot,
that did the trick

---

