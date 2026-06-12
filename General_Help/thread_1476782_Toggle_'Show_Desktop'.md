---
title: "Toggle 'Show Desktop'?"
date: 2010-05-08
forum: General Help
---

### Post by Artiom.Fiodorov on 2010-05-08
Hello! I got rid of my bottom panel, but I am still used to 'Show Desktop' button right in the bottom left corner. I was just thinking is it possible to Toggle 'Show Desktop' state just by moving my mouse in that corner?
I was thinking of using wmctrl and compiz commands edge biding, but my problem is that wmctrl has two different commands - one for showing desktop one for hiding. But I want to toggle. Any suggestions?
Alternatively I could get CTRL-ALT-D pressed every time I move my mouse there. Any ideas how to make it?

---

### Post by Artiom.Fiodorov on 2010-05-08
Found the solution. Ok here how I got it to work:
**UPDATED** [COLOR="Red"]use Bonster's solution instead[/COLOR]:
```
sudo apt-get install xautomation
```

[COLOR="Red"]Skip creating the script and just put this command in command 2 in CompizConfing[/COLOR]
```
xte 'keydown Control_L' 'keydown Alt_L' 'key D' 'keyup Control_L' 'keyup Alt_L'
```

This one is glitchy and it requires wmctrl to be installed:
```
sudo apt-get install wmctrl
```

```
#!/bin/bash
if test -e ~/.showdesk; then
  rm ~/.showdesk
  wmctrl -k off
else
  touch ~/.showdesk
  wmctrl -k on
fi
```

[COLOR="red"]SKIP[/COLOR] Create file 'toggledesktop' in you /home/Programs directory
[COLOR="Red"]SKIP[/COLOR] Put the script in this file, and tick 'Allow executing file as program' in it's properties.
Go to CompizConfing (Preferences->CompizConfig Setting Manager), commands,
write in command 2: ```
[s]/home/[username]/Programs/toggledesktop[/s]
xte 'keydown Control_L' 'keydown Alt_L' 'key D' 'keyup Control_L' 'keyup Alt_L'
```
in Edge binding tab select the corner you want to run command 2:

[IMG]http://img59.imageshack.us/img59/1416/compiz.png[/IMG]

And don't forget to set Edge Trigger Delay 400-500 in CompizConfig General options:

[IMG]http://img576.imageshack.us/img576/1416/compiz.png[/IMG]

and enable compiz (enabled by default in Preferences->Appearance->Visual Effects->Normal)

SOLVED

---

### Post by Bonster on 2010-05-08
wmctrl is usually glitchy for me, so u can try this one to toggle also

> sudo apt-get install xautomation

Then you can send the hotkey presses Ctrl+Alt+D using xte

> #!/bin/bash
xte 'keydown Control_L' 'keydown Alt_L' 'key D' 'keyup Control_L' 'keyup Alt_L'

---

### Post by linuxcss on 2010-05-08
i am using gconf-editor,  and karmic 

where do i find the edge-trigger setting?

---

### Post by Artiom.Fiodorov on 2010-05-08
Thanks Bonster
2linuxcss:
I updated the post

---

