---
title: "Same rar, separated in pieces with different password"
date: 2009-11-27
forum: General Help
---

### Post by Fixman on 2009-11-27
I recently ran into a little problem: I wanted to download a rar archive from Megaupload, that was split in many different parts (part01.rar, part02.rar, etc.). However, while I'm downloading them, for some reason Megaupload erased those links, so it wasn't possible to download them again.

I didn't find those files again on the Internet, however I found another split rar, with a different name, but of the same file (I can tell because it has the same number of parts, and every part has the same size as the first group). So I downloaded only the parts that I needed from the second links, only **to find out that the first links had a password, while the second didn't, so I can't extract the rars**.

Is there any way I can solve this without redownloading the files from the second group of links?

---

### Post by dcstar on 2009-11-27
> **Fixman said:**
> I recently ran into a little problem: I wanted to download a rar archive from Megaupload, that was split in many different parts (part01.rar, part02.rar, etc.). However, while I'm downloading them, for some reason Megaupload erased those links, so it wasn't possible to download them again.

I didn't find those files again on the Internet, however I found another split rar, with a different name, but of the same file (I can tell because it has the same number of parts, and every part has the same size as the first group). So I downloaded only the parts that I needed from the second links, only **to find out that the first links had a password, while the second didn't, so I can't extract the rars**.

Is there any way I can solve this without redownloading the files from the second group of links?

Split .rar files have to be joined **before** extraction.

---

### Post by thedarkfalcon on 2011-02-06
> **dcstar said:**
> Split .rar files have to be joined **before** extraction.
No they don't. Evidence of this is if you only have 4/5 parts of a rar archive you can choose the option "keep broken pieces" when extracting and it will extract 4/5ths of the file. Eg, if extracting a movie and you had the 4 first pieces you should be able to watch the first part of the movie using VLC.

But back to the original question that Fixman asked, is there a solution? I also have found myself in the same predicament. I know the file I want to extract from the different set of archives is the same as the CRC is the same. Perhaps is there a way of changing a rars password? You cannot do this anyway I know of in winrar, and I have not found any third party apps that have this function.

I was hoping that when winrar hit the rar with the different password it would simply ask me for the new password, however it didn't and just said at the end of extraction process, error wrong password.

Some people sugested extracting the rar with the different password and then recompressing it (to have the same password as the other rars), however this is not an option either as there is only one large file to be extracted from all the rars. Extracting it will cause the whole file to be extracted not only the piece that is in that rar.

Any suggestions welcome.

P.S filename example: 
example.part1.rar
example.part2.rar
etc

---

