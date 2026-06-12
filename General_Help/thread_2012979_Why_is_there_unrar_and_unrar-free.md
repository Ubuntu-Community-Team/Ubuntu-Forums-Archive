---
title: "Why is there unrar and unrar-free?"
date: 2012-06-30
forum: General Help
---

### Post by elore on 2012-06-30
The vrms program said that one of my non-free packages installed is unrar so I tried to replace it with unrar-free but that could not open one of my rar files. I found that there is unrar source code available here [http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)

So why do we have to have both unrar and unrar-free? Can't we use the source code to make a free version? It has a licence restriction saying that you can use the code but you must not use it to figure out how to write rar compression, only decompression.

---

### Post by dino99 on 2012-06-30
Can't handle some archives in the RAR 3.0 format, only the non-free "unrar" package can do that.

---

### Post by Redblade20XX on 2012-06-30
> **elore said:**
> So why do we have to have both unrar and unrar-free? Can't we use the source code to make a free version? It has a licence restriction saying that you can use the code but you must not use it to figure out how to write rar compression, only decompression.

Nope the official one is restricted in that sense. It is not truely open source as we cannot fully modify it and redistribute it due to the license. I believe that both options are given due to the fact that some people like to have their distro as free as possible from proprietary code.

-Red

---

### Post by elore on 2012-07-01
Thanks for your replies! I am assuming that the source code here can actually decompress RAR 3, I can't verify that myself.

I have included license.txt from the unrar source code at the end of this message. My understanding of it is that one is permitted to use and modify it for decompression but not compression. It is also required to include point 2 of the license text about it being forbidden to use this code to figure out how to do compression.

Now I hope someone could confirm or correct me on this because I am not certain, but it seems like you could create a GPL rar decompression from this source code as long as you also include the notes about not using it to create a compressor. Welcoming your input!

```
 ******    *****   ******   UnRAR - free utility for RAR archives
 **   **  **   **  **   **  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ******   *******  ******    License for use and distribution of
 **   **  **   **  **   **   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 **   **  **   **  **   **         FREE portable version
                                   ~~~~~~~~~~~~~~~~~~~~~

      The source code of UnRAR utility is freeware. This means:

   1. All copyrights to RAR and the utility UnRAR are exclusively
      owned by the author - Alexander Roshal.

   2. UnRAR source code may be used in any software to handle
      RAR archives without limitations free of charge, but cannot be
      used to develop RAR (WinRAR) compatible archiver and to
      re-create RAR compression algorithm, which is proprietary.
      Distribution of modified UnRAR source code in separate form
      or as a part of other software is permitted, provided that
      full text of this paragraph, starting from "UnRAR source code"
      words, is included in license, or in documentation if license
      is not available, and in source code comments of resulting package.

   3. The UnRAR utility may be freely distributed. It is allowed
      to distribute UnRAR inside of other software packages.

   4. THE RAR ARCHIVER AND THE UnRAR UTILITY ARE DISTRIBUTED "AS IS".
      NO WARRANTY OF ANY KIND IS EXPRESSED OR IMPLIED.  YOU USE AT 
      YOUR OWN RISK. THE AUTHOR WILL NOT BE LIABLE FOR DATA LOSS, 
      DAMAGES, LOSS OF PROFITS OR ANY OTHER KIND OF LOSS WHILE USING
      OR MISUSING THIS SOFTWARE.

   5. Installing and using the UnRAR utility signifies acceptance of
      these terms and conditions of the license.

   6. If you don't agree with terms of the license you must remove
      UnRAR files from your storage devices and cease to use the
      utility.

      Thank you for your interest in RAR and UnRAR.


                                            Alexander L. Roshal

```

---

