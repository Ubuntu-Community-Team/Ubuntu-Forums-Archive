---
title: "sound and program launch script"
date: 2009-06-25
forum: General Help
---

### Post by seven winter on 2009-06-25
Hi kinda new to ubuntu but steadily learning and i was wondering if any one could help me with a simple script to play a sound for when i open a certain program from a shortcut on the desktop. I have managed to create a launcher to play a sound by using (play "music/wavfile.wav") but where do i go from there in the script? how do i get it to open a specified program (say firefox) after or before the sound is played?  Can anyone help me out?
Ive got ubuntu jaunty if that matters at all?
Cheers

---

### Post by kaibob on 2009-06-25
You do not need a script to do what you want. For example, to play a WAV file and then open the leafpad text editor, the command in the launcher would be:

aplay /path/sound.wav ; leafpad

I read your post a few times and am not sure what you want to do. Perhaps you could provide a bit more detail.

EDIT: The above command works when entered in a terminal window and I thought it worked when entered in a launcher, but it seems not to work now as a launcher. I'll experiment a bit more to see why. If this won't work from a launcher, a very simple shell script will do the job.

---

### Post by seven winter on 2009-06-25
Haha, nice one mate, cheers for that, that is exactly what i wanted to do, thanks for the quick reply btw kaibob.
Cheers

---

### Post by seven winter on 2009-06-25
Sorry mate, it works in when i write it in the terminal (plays sound and launches program) but when i put it in the command line in the new program launcher it doesnt do anything, just plays the sound but doesnt open the program!
Any help mate?

---

### Post by kaibob on 2009-06-25
> **seven winter said:**
> Sorry mate, it works in when i write it in the terminal (plays sound and launches program) but when i put it in the command line in the new program launcher it doesnt do anything, just plays the sound but doesnt open the program!
Any help mate?
I discovered that issue after my initial post in this thread. I don't know why that doesn't work.

I created the following shell script and then ran the shell script as a launcher. That does work.

```
#!/bin/bash

aplay /path/sound.wav ; leafpad
```

The above shell script runs aplay and then leafpad. An alternative that may work better is:

```
#!/bin/bash

aplay /path/sound.wav &

leafpad &
```

I tried these shell scripts with firefox rather than leafpad, and both work there as well.

---

### Post by seven winter on 2009-06-25
Thanks mate but how do i use it? create a launcher and type the script in the command line? or save it as a text file? if i have to save it in a text file how do i make it a launcher?
Could u give me a quick run through of the process please? sorry but im new to all this.

---

### Post by kaibob on 2009-06-25
Try this:

1) Create a directory in your home directory with the name "bin" (omit quotes). This is most easily done with Nautilus. 

2) Create a text file with gedit or other text editor. Paste the following code into the text file (change /path to whatever is applicable). Save the text file in the newly created bin directory with the name myscript.

```
#!/bin/bash
aplay /path/sound.wav &
firefox &
```

3) Open Nautilus and navigate to and right-click on the myscript file. Select Properties and then click on the Permissions tab. Put a check mark next to "Allow executing file as program." 

4) Create a launcher with the following commandline (change username to whatever is applicable):

```
/home/username/bin/myscript
```

5) Try the launcher. You may have to reboot or log out/in.

---

### Post by seven winter on 2009-06-25
Haha sorted cheers kaibob, and congrats on the 1000 posts mate.

---

### Post by loomsen on 2009-06-25
(and don't forget to add some useful things to the script,like

exit $?

so it won't become a zombie if something goes wrong...)

---

