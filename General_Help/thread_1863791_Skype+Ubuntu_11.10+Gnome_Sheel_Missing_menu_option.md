---
title: "Skype+Ubuntu 11.10+Gnome Sheel: Missing menu option in Sound Recorder"
date: 2011-10-18
forum: General Help
---

### Post by Bjorg on 2011-10-18
Hello:

I am using:
-Ubuntu 11.10
-Skype
-PS3 Eye Toy camera to input video and sound

This setup has been properly working in former Ubuntu releases.

To use the mic already built in on the PS3 Eye Toy camera I open de Sound Recorder app (notice: not inside Skype, from inside Skype it is not possible to do this) that is included in Gnome and then I go to File>Sound Mixer, from this menu I can choose Gnome to get the input audio from the PS3 Eye Toy, instead of from the Audio-In of the computer.

Now in Ubuntu 11.10 this Sound Mixer menu inside Sound Recorder is missing, Gnome says something like this: gnome-volume-control is not installed in the proper directory 

Note: I have tried this on Unity, Unity 2D, Gnome Classic, Gnome Classic 2D and Gnome Shell. In all of them the problem is the same.

What can I do? Basically what I want to do is to be able to tell the computer to get the audio in from the PS3 Camera.

Thanks in advance:

---

### Post by antimirov on 2011-11-12
The same story here. It worked for me in all Ubuntu versions since January 2010 and now with 11.10 it's not in the "Input devices". So let's try to solve this problem together, fellow victim.

---

### Post by antimirov on 2011-11-17
Created a bug at Launchpad - [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/889624](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/889624)

---

