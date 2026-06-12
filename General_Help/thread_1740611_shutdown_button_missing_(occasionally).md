---
title: "shutdown button missing (occasionally)"
date: 2011-04-27
forum: General Help
---

### Post by mabever on 2011-04-27
Hi all,

I installed ubuntu v10.10 about a month ago. A couple of times in the past week the shutdown icon hasn't appeared in the top right hand corner, but the user name has half appeared twice.

I've shutdown using the terminal as a get around.

Has anyone else experienced this? Is it a bug? and (finally) should I report it?

Next time it happens I'll take a screen shot and post.

Cheers,
M

---

### Post by horace on 2011-04-27
> **mabever said:**
> Has anyone else experienced this? Is it a bug? and (finally) should I report it?

I saw this happen last week - when I tried moving the panel to a different location the button re-appeared and was still there when I put the panel back at the top of the screen.

So it looks like it is a bug.

---

### Post by Silent Warrior on 2011-04-27
This has been reported in the past, unless my mind deceives me. I think the fix is to restart gnome-panel, like so:
```
sudo pkill gnome-panel && gnome-panel
```

---

### Post by holadebob on 2011-04-27
This problem has been report many, many times. I have Ubuntu 10.04 and this problem occurs about once or twice a week. Last night, after configuring the printer for a job, it happened again.

Sure it's easy to restart Ubuntu with the terminal, reset the panel, etc., but it would be reallly nice if one of those who know out there would tell us how to avoid the problem.

:)

---

### Post by whitefort on 2011-04-27
I get this problem once every couple of days.

I eventually got fed up and added another shutdown button to the other panel.  Not the most elegant solution, but it means I always have at least ONE shutdown button when I want it!

---

### Post by KegHead on 2011-04-27
Hi!

I've only seen this after an update.

Just restart!

KegHead

---

### Post by holadebob on 2011-04-27
If we could eliminate the shutdown button on the upper panel and install one on the lower, that would be cool, but I don't think it's possible to eliminate the upper panel shutdown options button. It seems a good functional solution to install another on the bottom panel and just ignore the other.  

The upper panel right hand corner shutdown button option seems to have been a good idea. 

It's easy to run sudo shutdown now in the terminal, and that's what I have been doing.

I'm going to try making more buttons.

---

### Post by mabever on 2011-04-27
Thanks all, sounds like I'm just going to have to live with it.

M

---

### Post by jespdj on 2011-04-27
I also occasionally get this. It's most likely a bug.

> **mabever said:**
> Thanks all, sounds like I'm just going to have to live with it.
Why? Report it. If nobody reports a bug then it will never be solved and then you'd indeed have to live with it.

If the button is not there you can shutdown by entering the command "sudo shutdown now" in a terminal window.

---

### Post by holadebob on 2011-04-28
Anyone know if the same problem happens on Linux Mint?

---

### Post by pqwoerituytrueiwoq on 2011-04-28
you could set a hotkey to restart the panels
[FONT=Courier New]killall gnome-panel[/FONT]
system->preferences->keyboard shortcuts

---

### Post by AgentZ86 on 2011-04-30
> **Silent Warrior said:**
> This has been reported in the past, unless my mind deceives me. I think the fix is to restart gnome-panel, like so:
```
sudo pkill gnome-panel && gnome-panel
```

This got rid of all my panels now I can't even access the terminal

---

### Post by grahammechanical on 2011-04-30
I did not actually fix this but I was able to add a shutdown icon to the panel. Right click and select Add to panel and select Shut Down from the list. It has a square red icon. click on that and it will give you shutdown options.

Regards.

---

### Post by AgentZ86 on 2011-04-30
I'm missing shutdown button, and the wired connection for ether net

Not sure why
It appears to be gone permanently after today

Was there last night and this morning they are gone

---

### Post by AgentZ86 on 2011-04-30
I found this to fix mine:

[http://www.troublefixers.com/restore-recover-deleted-ubuntu-top-panel/](http://www.troublefixers.com/restore-recover-deleted-ubuntu-top-panel/)

I noticed there is a panel break to keep things to the right of my top panel, when I do notice that items are missing this break it missing too I'm sure something to do with that break.

Anyhow the commands say fixes deleted panel but actually it brought back everything that I was missing

Anyhow happy hacking

---

