---
title: "Scripting screen"
date: 2009-10-10
forum: General Help
---

### Post by gunksta on 2009-10-10
**Scripting screen**             
                                                                I am trying to write a script to affect an active screen session. I've got 90% of it figured out but I can't seem to beat this last 10%. This is what I would like it to do.

[LIST=1]
[*]Open a new screen and make it active
[*]display the contents of a variable $RHELPFILE
[*]name the active screen, using the contents of $XTT
[*]when exiting the pager, delete the screen. Do not return the user to the bash prompt.
[/LIST]

What I have below will do steps 1-3. But, I'm not sure how to write it so that screen will delete the pager screen when exiting the pager. Right now if a user selects "q", less will exit, returning the user to the bash prompt, which is the problem. I want bash to immediately exit and have screen close out the screen, returning the user to the previous screen.

```
              
screen -X screen && screen -X exec less $RHELPFILE && screen -X title "R Help - $XTT"

```

---

