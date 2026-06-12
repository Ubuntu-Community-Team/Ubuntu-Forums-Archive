---
title: "Application to slow down songs"
date: 2010-01-21
forum: General Help
---

### Post by JimBuntu on 2010-01-21
Is there any apps for Ubuntu that can play a song at a slower speed yet keep the tone (like windows media player)? For instance I want to play a song at half speed so I can learn the guitar part... I have done this with windows.

---

### Post by ibuclaw on 2010-01-21
Train your ears, and learn songs by listening to them at full speed. That is what I do.

But, if you haven't been at it for 7+ years, I suppose I wouldn't bite you for giving [Audacity]("http://audacity.sourceforge.net/") a try. ;)

HowTO:
Press ctrl-a to select the whole track

Then select change tempo from the edit menu, then pick a number to change to and from.

Regards
Iain

---

### Post by joeblurton on 2010-01-21
A little bit of Googling brought up [Yet Another Time Machine]("http://www.filetransit.com/view.php?id=92513"), but it's a command line player. Still, it might be more in tune with KISS (the saying, not the band!) than using Audacity...

---

### Post by tgalati4 on 2010-01-21
sudo apt-get install sox
man sox

Use the tempo switch:

       tempo [-q] factor [segment [search [overlap]]]
              Change the audio tempo  (but  not  its  pitch).   The  audio  is
              chopped  up  into  segments  which  are then shifted in the time
              domain  and  overlapped  (cross-faded)  at  points  where  their
              waveforms  are  most  similar  (as  determined by measurement of
              &#8216;least squares&#8217;).

Update:  I tried VLC and there's no option when playing an mp3.  If you have a *.wav file and you install sox then you can simply:

play your_next_big_hit.wav tempo 0.5

1/2 tempo is pushing the limits of the algorithm, but you can try 0.75 or any other value less than 1.0 to slow the track down.

---

### Post by junapp on 2010-01-21
doesn't vlc allow you to do this?
it is in the repos I believe.
Playback -> Slower.

---

