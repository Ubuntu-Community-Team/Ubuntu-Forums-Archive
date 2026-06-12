---
title: "Compression excluding certain ascii characters"
date: 2011-06-08
forum: General Help
---

### Post by afischer.aea on 2011-06-08
Hey all,

I am working on a project where I am dialing out of a modem!! Old stuff, ya, but the modem allows my device send info from remote sites from my datibase through a phone line so that this IT departments dont have to worry my device being a security issue on their networks.  

Any way, the modem I'm using isn't incredibly well designed, and when a certain ascii char is read by the modem, it reads it as an EOF indicator.  It is also important that the files I send are compressed.

My question is:  Does anyone know of a compression format that allows ME to dissallow IT's use of certain ascii chars?  


just as an illustration:

Device --------> Modem ---------> Off-site

and the Modem stops talking to the device when a certain char is passed to it.

Thanks in advance!

---

### Post by Vaphell on 2011-06-08
how big are the chunks of data to send?
if not so big then it could be worthwhile to:
- find any n-byte sequence that does not exist in original compressed data (of course n and sequence can't hold the magic value)
- replace any occurence of the magic char with the sequence
- use n and the sequence itself to create a header in front of the modified data
- at the other side extract n and sequence, perform a reverse operation of substitution, decompress data

---

