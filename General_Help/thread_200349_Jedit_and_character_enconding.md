---
title: "Jedit and character enconding"
date: 2006-06-20
forum: General Help
---

### Post by bohboh on 2006-06-20
I have a php file which has the character "&#1024;".

In jedit it is displaying as a square whereas in windows, dreaweaver mx it is displaying ok.

Is this to do with character encoding? What should it need to be?

---

### Post by Marshall2day on 2006-06-20
To display this character, I think you'll need unicode encoding

---

### Post by bohboh on 2006-06-20
[QUOTE=Marshall2day]To display this character, I think you'll need unicode encoding[/QUOTE]

I dont really understand encodings generally.
When you say i need unicode encoding, are you referring to UTF?
It is already UTF-8.

---

### Post by Marshall2day on 2006-06-22
You'll probably need UTF-16. This actually means that every character is using 16 bits or 2 bytes. Therefore you can display a lot more characters. 

With 8bits you can display 2^8 or 256 different chars while with 16 bits, you can display 2^16 or 65536 different chars. You can see that this is a huge difference. The downside of all this, is that a 16bit encoded file will take twice as much diskspace as an 8 bit encoded file.

---

