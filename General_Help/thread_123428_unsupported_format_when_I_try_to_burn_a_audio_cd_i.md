---
title: "unsupported format when I try to burn a audio cd in K3b"
date: 2006-01-30
forum: General Help
---

### Post by taseal on 2006-01-30
I have some songs that I'd like to burn to an audio cd, but it will not burn them because it cant 'convert' the songs to .wav format... k3b says

'Unable to handle the following files due to unsupported format'

how am I going to convert these things?

:(

---

### Post by kingsidy on 2006-01-30
install audio codecs using automatix. if you want k3b to handle mp3s install the k3b-mp3 package from synaptic

---

### Post by ewr2san on 2008-05-13
The new package that fixes this in Ubuntu 8.04 (Gutsy) is the libk3b2-extracodecs package.

---

### Post by Wangberg on 2008-05-19
> **ewr2san said:**
> The new package that fixes this in Ubuntu 8.04 (Gutsy) is the libk3b2-extracodecs package.

I have tried this to no avail.  I get the same error as taseal.  

I converted .mp3 to .wav using Sound Converter, and receive this same error message when trying to add the .wav files to an Audio CD with K3B.  

Any ideas???

---

### Post by Giannis68 on 2008-05-25
> **Wangberg said:**
> I have tried this to no avail.  I get the same error as taseal.  

I converted .mp3 to .wav using Sound Converter, and receive this same error message when trying to add the .wav files to an Audio CD with K3B.  

Any ideas???
the same problem when i try to add [COLOR=Red].wav[/COLOR] files
[COLOR=Red]Unable to handle the following files due to an unsupported format:[/COLOR]
You may manually [COLOR=Red]convert these audio files to wave[/COLOR] using another application supporting the audio format and then add the wave files to the K3b project.

---

### Post by konungursvia on 2008-05-25
Did you try reinstalling gstreamer?

---

