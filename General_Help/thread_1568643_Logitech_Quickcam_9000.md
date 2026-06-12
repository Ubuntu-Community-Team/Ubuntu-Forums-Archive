---
title: "Logitech Quickcam 9000 ???"
date: 2010-09-05
forum: General Help
---

### Post by karlm on 2010-09-05
Hi all,

I've just recently converted to Linux after a very harsh viral attack on my Windoze system which completely wiped out even the anti-virus package I had.

Anyway, I have an overseas daughter and the webcam is my only means of contact with her... So I could REALLY do with a hand understanding how to make my webcam work, please?

I'm quite good with Windoze systems, but Linux is new to me... so please take it easy on the terminology for me.

Thank you :)

---

### Post by hwttdz on 2010-09-05
First thing to try is to make sure the webcam is working, so plug it in and get a terminal (applications, accessories, terminal).  Then type in just the word "cheese" and press enter.  This will start the program cheese, which is really one of the simplest webcam programs (if you're greeted with "cheese is not installed", do "sudo apt-get install cheese", then try again).  If you see a live picture of yourself great, otherwise we need to try something else.  

Then I'd start up pavucontrol (you may need to install this one as well), and skype (if that's the program you're looking to use, I'm not sure if it's in the repo currently, but you can download it from their site).  Start pavucontrol (same way as cheese), and move over to the recording tab.  You'll see a skype "input from" and change that to your microphone of choice (you can see your microphone options on the input devices tab.  Change skype to the input device you want. Then adjust the volume (I shove it up all the way, as it's easier for someone on the other end to turn the volume of an application down if you're too loud than the reverse).  And if you can both hear a test call and hear your recording you're good to go.  

Also skype options can be found under the blue icon in the bottom left of the skype window (took me longer than I care to admit to find that one).

---

### Post by karlm on 2010-09-05
Thank you, Sir! It's working... and some of the cheese effects are ... uh... worrying lol

---

### Post by sandyd on 2010-09-05
nvm

---

