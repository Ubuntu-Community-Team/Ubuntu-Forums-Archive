---
title: "File magic number, signature and hex"
date: 2011-09-06
forum: General Help
---

### Post by hyperhelium on 2011-09-06
Hello everybody.

I hope somebody can help me out this. I am planning to recover some accidentally deleted files from an external HD. I have used photorec and scalpel, but it seems I am having trouble with the files signatures, magic numbers and hex.

The problem is the files I am trying to recover are ".tar.bz2" and ".tar.gz" and even though the Photorec manual says it recognizes them, it doesn't seem to. I am only getting a large bunch of files with nothing in them. I think .bz2/.gz have different signatures than .tar.bz2 and .tar.gz

I have also used scalpel, but it seems I didn't use the correct "file signature, magic number and hex" to have scalpel identify them. Photorec says it comes with a utility named "fidentify" to identify that information, but it really doesn't (at least not in the linux version) it says that command is similar to the "file" unix command, but I don't know how to use it. Specifically, Photorec says:

The file must contain one signature definition per line. A signature is composed of 
 
[LIST]
[*] extension name
[*] offset of the signature
[*] signature or magic value
[/LIST]
 The magic value can be composed of 
 
[LIST]
[*] a string, ie "data". Special characters can be escaped like "\b", "\n", "\r", "\t", "\0" or "\\".
[*] hexadecimal data, ie 0x12, 0x1234, 0x123456... Note that 0x123456, 0x12 0x34 0x56 and 0x12, 0x34, 0x56are equivalents.
[*] space or comma delimiters are ignored
[/LIST]
 By using an hexadecimal editor, you can see that the pfi file from our example begins by a distinctive string.


You can see the manual explaining this here:


[http://www.cgsecurity.org/wiki/Add_your_own_extension_to_PhotoRec](http://www.cgsecurity.org/wiki/Add_your_own_extension_to_PhotoRec)


I am totally lost!! I don't know what they are talking about, since I am not an expert in forensics or an engineer... I'm just a simple user. So, if anyone can help me with this I would really appreciate it. In sum:
What are those values (signature, magic number, hex) for "tar.bz2 and tar.gz"?? What should I put????


Thank you very much.

---

### Post by hyperhelium on 2011-09-11
Bump... Please help... :S

---

### Post by hyperhelium on 2011-09-14
Bump again

---

### Post by hyperhelium on 2011-09-20
Well it seems I'm having no luck with this one. I might just change the question. What is a file header and footer??

Tx in advance.

---

### Post by lqbweb on 2011-10-14
this is because the photorec version in the Ubuntu repositories is currently 6.11, and fidentify is only attached from the 6.12, since it is the first supporting custom signatures

---

