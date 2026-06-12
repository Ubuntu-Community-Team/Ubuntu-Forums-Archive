---
title: "Guitar chords from mp3"
date: 2009-08-23
forum: General Help
---

### Post by 73ckn797 on 2009-08-23
Is there a Linux program that will be able to pick up chords from a song?

I have an old Windows program but no longer have Windows.

---

### Post by tgalati4 on 2009-08-23
I don't know how the windows program worked, but gtkguitune can pick out keynotes from an input stream.

sudo apt-get install gtkguitune

If it's a popular song, there are plenty of tabbing websites.

---

### Post by 73ckn797 on 2009-08-23
> **tgalati4 said:**
> I don't know how the windows program worked, but gtkguitune can pick out keynotes from an input stream.

sudo apt-get install gtkguitune

If it's a popular song, there are plenty of tabbing websites.

I loaded the program but there are no options to play anything. Guess that I will have to look around for more info to use the program.

The song is not popular at all and is 20 years old. I have been looking for a very long time. I am aware of the many tab sites out there and use them a lot.

The song is by Dion Dimucci: "He's In You".

---

### Post by tgalati4 on 2009-08-23
gtkguitune takes a microphone or line input and picks out the major keys.  You need to adjust your mixer settings (including the capture sliders) to monitor what is playing from the pcm or master channel.

When you play your mp3, you should see signal bars in the program and the keys will be highlighted.  Write quickly!

An alternative is to use audacity.  Highlight a snippet of the music and play it back repeatedly.  With guitar in hand, tab it manually.

There may be an audacity filter that does some crude tabbing, I don't know you would have to research it.

---

