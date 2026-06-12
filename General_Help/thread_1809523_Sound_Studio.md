---
title: "Sound Studio"
date: 2011-07-21
forum: General Help
---

### Post by p3aul on 2011-07-21
Now that I have downloaded and extracted Sound Studio, how do I install and run it?
Thanks,
Paul

---

### Post by MG&amp;TL on 2011-07-21
A link to the site would help, but if you got it in tarball format, generally ; (in terminal)

 cd to the folder where you extracted it to.

 type ./configure
 type ./make
 type sudo make install

An easier option would be audacity if you want a sound mixer/recorder/editor. It's in Software centre. 

If you want more specific advice (e.g. how to use the terminal commands,) just repost.

---

### Post by p3aul on 2011-07-21
Well I have Audacity but it won't "Record What U Here" Some one here gave me a script to use Sox to do the recording and it works fine, except I have to run the script and it captures the audio I want the writes it to a wav file and then exits when I press Ctrl-C. I works great but is some what tedious to use since I have to rename the file edit it( To remove dead space at begin and end) then save it as an mp3 file in my music folder.

In Win 7 I used Audacity and had no problem capturing the audio and saving as an mp3 file. I couldn't get Ubuntu to do that so I ask the question here and a kind person came to my aid by writing the Sox script.

I read that that Sound Studio uses Sox and I ?don't? think Audacity does. Anyway I was hoping that Sound Studio might allow me both to edit and record what I here.
Thanks,
Paul

---

### Post by p3aul on 2011-07-21
> type ./configure
 type ./make
 type sudo make install

Here is what I get after typing each command:

$ ./configure  **[COLOR=Red]No such file or directory[/COLOR]**
$ ./make  [B][COLOR=Red]No such file or directory
[/COLOR][/B][COLOR=Red][COLOR=Black]$ sudo make install   [COLOR=Red][B]password for p3aul: 
make: *** No rule to make target `install'.  Stop.
p3aul@p3aul-Aspire-X3910:~/SoundStudio/SoundStudio$ 

[/B][COLOR=Black]It sure bumfuzzels me!

[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Mr. Shannon on 2011-07-22
Here is a video tutorial on how to record what you hear in Ubuntu: [http://www.youtube.com/watch?v=AJO5rHI6akM]("http://www.youtube.com/watch?v=AJO5rHI6akM")

You can even use Audacity with the method above.

If you still want to install Sound Studio then give us the link so we can look at it to see how to install it.

---

### Post by MG&amp;TL on 2011-07-22
I personally have 'recorded what I hear' in Audacity. Just to see if it helps. :D

Or alternatively, you could use one of the many recording programs, save it to something like a .wav or whatever, and import it into Audacity.

---

### Post by haqking on 2011-07-22
if you are refeering to sound studio 1.06 for linux.

i just downloaded the .tar. extracted it

there is a readme in there with instructions

---

### Post by p3aul on 2011-07-22
Thanks for the replies. I will first try the Youtube video. In fact, I prefer Audacity. I will keep y'all posted!
Paul

---

### Post by p3aul on 2011-07-24
Ok, I watched the video, It was pretty amateurish, but I finally was able to reason it out. It seems I can use Audacity, If I open this Pulse Audio Volume Control at the same time. It's not perfect, but it eliminates a couple of steps any way. 
Thanks for the replies and the suggestions folks!:P
Paul

---

