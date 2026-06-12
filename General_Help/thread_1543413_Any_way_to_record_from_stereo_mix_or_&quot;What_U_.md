---
title: "Any way to record from stereo mix or &quot;What U Hear?&quot;"
date: 2010-08-01
forum: General Help
---

### Post by L a r r y on 2010-08-01
**Or alternatively, to play sound with one program from one sound card and record sound with another program?**

In Windows I could record directly off the stereo mix, and thus be able to play a sound file and at the same time put it out over a chat room.

My project involves playing a recorded news file over EchoLink, which involves amateur radio links over the Internet.

I am running EchoLink, a Windows program under Wine, and playing an amateur radio news file over the Banshee Media Player.

Alternatively, I could play it over the Movie Player, or Rhythmbox, or Winamp, another Windows program.

One difference between Windows and Ubuntu is that I can play two recorded pieces at the same time with two different programs, whereas in Windows the sound card is already in use.

Another difference is that aftermarket sound cards let you record from what plays over the speakers ("Stereo mix," "What U Hear") in Windows and apparently not in Ubuntu.

I thought I might be able to do this by playing over one sound card and coupling its output to a line input of the other sound card.  Preferably play a news audio file using a media player on one card and operate the chat room software, or EchoLink on the other card.

10.04 lets me set which card is my default from the volume control preferences.

I have seen postings that allowed people to accomplish this under earlier versions of Ubuntu by running ```

 sudo apt-get install asoundconf-gtk

```
but this installation adds a "Default Sound Card" option to the Preferences menu under System.  The option does not start, so I think its usefulness ended with later versions of Ubuntu.  It was supposed to provide a drop-down menu letting me choose which sound card to use as default.  The O.P. wanted the Orca screen reader to send output to a different card, or wanted a different card for Skype, so that everything but Skype plays over speakers, and Skype plays through headphones plugged in to the other card.

**Has anyone done anything along this line on version 10.04 of Ubuntu?  If so, how was it done?**

Another posting introduced the use of two bash scripts, one set to make "this" card the default, the other set to make "that" card the default through the use of a mouse click on the appropriate launch icon.  This, however, does not make different programs use different cards.

---

### Post by Dustin2128 on 2010-08-01
I'm sorry your post was a bit unclear, are you asking how to record what you're listening to on the desktop for future replay?

---

### Post by bobcollard on 2010-08-01
Try Audacity.

---

### Post by L a r r y on 2010-08-01
> **Dustin2128 said:**
> I'm sorry your post was a bit unclear, are you asking how to record what you're listening to on the desktop for future replay?

You are right, if I can record what I am listening to on my desktop, I can also play what I am listening to from my desktop to a chat room audience, Skype contact, EchoLink contact and so on.


I would un-mute the microphone on the playback panel, and select Stereo Mix as my source instead of microphone-in or line-in on the recording panel.  Then I would be able to speak through the microphone, but also be able to play a sound recording from a media player.

I, of course, would have to be careful of not using excessive microphone gain or excessive speaker volume to not set up a feedback loop.  Adjusting speaker volume has no effect on the level feeding the recording input from Stereo Mix.  There is a separate input gain control for stereo mix on the recording panel.

This is a description of the way it works in Windows XP, and if I can rig it up to accomplish this in Ubuntu, then I have met my needs.

Another way to do it would involve an outboard mixer, mixing in my speaker output and my microphone and feeding the mixer output to the line-in on the sound card.  It would take more hardware, but it can be done.  To do that I'm going to have to come up with some 9-volt batteries and audio cables.

---

### Post by bobcollard on 2010-08-01
Audacity works as a recorder and a mixer.

---

### Post by L a r r y on 2010-08-01
> **bobcollard said:**
> Audacity works as a recorder and a mixer.

Audacity is a sound recorder and editor.  You can edit a pre-recorded piece and dub in a voice-over and save the new recording.  You can play the recording over your speakers.


I am using VOIP, voice over IP, software.  This software lets me use the mic input or Line input on my sound card from external sources (radio, CD player, microphone, to name a few) and I can transmit that information over the Internet to the other end of the communications link.

In aftermarket sound cards, purchased at retail and added to the original computer configuration, when running Windows as the OS, one may select any number of devices as the input:  Wav out, midi out, or a selection that captures whatever is playing on the speakers, in addition to the mic input and Line input.

Some, but definitely not most, off-the-shelf computers with sound built-in do not offer the option of selecting what is playing over the speakers.

So far, I have not seen the capability, even though it exists in the hardware, to select what is being played over the speakers in Ubuntu.


Alternatively, if I could have one program play out over one sound card, and have the rest play out over a second card, I could route the output of the first card to the input of the second and I would be able to record a copy of it, or play it over the VOIP circuit.


So far, I have been able to select which card to use for all programs.  All programs use the same card, regardless of which one it is.

I can select output from one card and input from another, I think,  but all programs output on the same card.  Were I to feed output to input, it would be no different than if I feed output of the card to its own input.

In Windows with capable sound cards, I can select to un-mute the microphone over the playback channel.  With this, I could play music and sing karaoke with it and have my karaoke session be heard over the speakers.

But also with this capability I can play the pre-recorded and live microphone over the VOIP circuit.

I do not see an option to allow the microphone to play over the speakers in Ubuntu.


If I could achieve what I want to do with VOIP, I would be able to record myself singing with the music in Audacity for later playback.  

I hope I have better explained what I am trying to do here.

**Has anybody got ideas of how I can achieve my goal?**  All comments or questions are welcome.


I want to be able to mix pre-recorded material with my live voice for real-time use in a VOIP conversation.

---

### Post by TheGeezer on 2010-09-13
bump.

there are a few areas where this is useful/fun:
1. karaoke
2. having phone with a microphone and milkdrop
3. playing mp3 files down a headset when talking to someone in a program that would otherwise not be able to play music.
e.g. skype
4. attaching DJ decks to a laptop and open "linein://"  
(that's how i'd do it in winamp... still looking for a way of doing this in qmmp/xmms etc.)
5. recording stories and having the sound effects queued up in an mp3 player, all you have to do is read the story and press play/next every now and then.
6. creating horrible feedback squeals to scare the cat with
7. recording conversations on voip 

yes you can do it with a specific app or use a software to overlay for later editing, but with a full stereo mix you can do what u like.

it's not exactly something that is critical to the operation of an OS, but it does seem kinda odd that buntu doesn't seem to have a 'full' mixer control; windoze can do it! 

is this in ALSA thing? cos alsamixer doesn't have microphone/line input as an option in playback

thanks to anyone who can help overcome this little nuisance.

---

### Post by TheGeezer on 2010-09-13
have found this which works and shows it is possible
[http://stream-recorder.com/forum/no-stereo-mix-solve-audacity-recording-problem-t7260.html?](http://stream-recorder.com/forum/no-stereo-mix-solve-audacity-recording-problem-t7260.html?)

but - this uses the pulsemixer to monitor the recording; can we skip the record wiht audacity step and just monitor does anyone know?

looking at [http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules) 
and it seems that pulseaudio and jackd provide all the flexibility i could ever want; now just to find a GUI for these tools?  or if anyone can beam over a sensible howto that would be incredible


thanks in advance :)

---

