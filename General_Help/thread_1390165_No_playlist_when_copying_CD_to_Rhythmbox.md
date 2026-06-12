---
title: "No playlist when copying CD to Rhythmbox"
date: 2010-01-25
forum: General Help
---

### Post by Scunnered on 2010-01-25
I recently bought a CD which I wanted to add to Rhythmbox only to find that the playlist did not properly list the tracks and their details.

If I use the CD player and open with Rhythmbox it will properly display all the information however if I attempt to copy all the tracks from the CD to my music folder it will do no but will not provide track information

One thing that I have noted is that all my files in my music folder are .flac whilst those on the CD are .wav and these also display a lock against each.

Can anyone offer guidance on this.  Will I be able to copy and display the track information over to my music folder or am I forever going to be forced to play directly from the CD?  Alternatively is there some way having opened the disc with Rhythmbox to then save it there and then add my music folder to join up with the CD which has been saved.

Your assistance will be appreciated as it is frustrating to say the least at the moment having to fiddle about between a CD and my music folder.

---

### Post by mcduck on 2010-01-25
How are you importing the tracks to your computer?

For audio-CD's the track information can easily be automatically searched from the Internet based on track count and their lengths, but such approach doesn't work for compressed audio files so the metadata has to be saved to the files when you create them.  Adding the data afterwards is a lot harder thing to do and usually requires more or less writing the tags by hand.

Perhaps you haven't enabled saving metadata to .flac files in the program you used? While tags in mp3 files are very common (just like mp3 files themselves), flac is a bit less common format and it's tags aren't as widely supported in different programs.

---

### Post by Scunnered on 2010-01-26
**mcduck**

Many thanks for your reply.  Sorry for the delay in replying but as you can see I am in deep trouble. 

You fairly know how to set the cat amongst the pigeons by asking how are you importing the tracks to your computer?

I had thought that all I had to do was to copy the tracks on the CD to the my music folder and obviously from events I was wrong.  I went back some time and had a look at a question I raised when I initially started using Ubuntu and found reference to using the **Audio CD Extractor** but looking for this in the various packages brought no result.  Google came up with the response of Sound Juicer but everything there was for very early versions 7.10 being the last.

This now poses the question of how do I now extract tracks from a CD to my music now?

One thing that puzzled me was that I could open up the CD and listen to it in Rhythmbox but could not save it alongside earlier saved tracks. Nor would all the tracks load back into Rhythmbox when I deleted everything and attempted to reinstall them. 

Your kind assistance will be most appreciated.

---

### Post by mcduck on 2010-01-27
The easiest way would probably be to rip the tracks into your computer with Rhythmbox. To do that all you ened to do is to open Rhythmbox, then right-click your audio-CD's icon in the left side panel and select "Extract to Library". Or click the "Copy all tracks to library"-icon in the toolbar.

You can select what format Rhythmbox uses to import your music by going to Edit/Preferences, and on the Music-tab you'll find a dropdown box where you can choose the file type, as well as where Rhythmbox keeps your library and how the files should be named.

Sound Juicer is also a nice one, and it's defeinitely available for all Ubuntu versions. Just install it from Ubuntu's repositories with your favoutite package management tool (Ubutnu Software Center/Synaptic/apt-get).

---

### Post by Scunnered on 2010-01-27
**mcduck**

Many thanks for your advice.  No wonder I could not find how to copy over to the Rhythmbox.  I looked everywhere but where you directed me.  

As I port I am copying the CD and am looking forward to having the Planet Suite available along with my other music.

Again my sincere thanks for all your kind assistance

---

