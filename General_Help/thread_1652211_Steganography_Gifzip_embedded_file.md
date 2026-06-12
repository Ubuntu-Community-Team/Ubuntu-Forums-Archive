---
title: "Steganography: Gif/zip embedded file"
date: 2010-12-24
forum: General Help
---

### Post by J V on 2010-12-24
Gif files display their length at the start of the file, and zip files have a table with the locations of the files at the end of the file. By combining the two it's possible to create a gif file which, when opened in an archive manager, contains hidden files.

How would I go about doing this? Do I have to learn the zip standard and manually graft the files together in a hex editor?

Edit: Solved!

```
cat input.jpg input.zip > output.jpg
```The zip table must show the file location as an offset to the central directory. COOL

---

### Post by J V on 2010-12-24
I'm changing this to unsolved. While this method should work with pngs, jpgs, and gifs, I can't get it to work on a png. (And haven't tested a jpg).

Edit: Ok, I've tried the png, it appears it works fine with small pngs but not with large ones. Anyone know why? Hex editor doesn't show any difference. CLI unzip shows the same error both times (#### extra bytes at beginning or within zipfile) but handles it fine, is this just an error with file roller?

Does file roller use p7zip as the backend if it's not installed? How can I switch it back to the default?

---

