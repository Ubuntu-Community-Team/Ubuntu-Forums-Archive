---
title: "recordmydesktop problem"
date: 2009-09-20
forum: General Help
---

### Post by mihael032 on 2009-09-20
hi all :) lm new to ubuntu lm using it couple days  l have a question about gtk-recordmydesktop ( for recording your desktop , name tells u all :P)

it worked when l instaled it but next time l ran it and started to record  some error opens 

it writes something like this  :      RECORDING IS FINISHED
                                                                        recordMyDesktop has exited with status: 768
                                                                     Descreption: could not open/configure sound card


l dont understand why it hapents it worked be4 :(

---

### Post by elliotn on 2009-09-20
removing and reinstalling stuff always work for me

---

### Post by pcjunkie on 2009-09-20
Record has an issue with ALSA. 
If something else attempts to open a sound port RecMyDesktop will fail.

ie it won't work with flash or anything else that uses sound.
I found using sound recorder does work so I make video and sound separately.Using a video editor you simply drop the sound track in.

Remember to give yourself a cue marker.

---

