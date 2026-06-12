---
title: "Hiding known filetype extensions &amp; Open With Option tweak"
date: 2009-10-20
forum: General Help
---

### Post by neon100 on 2009-10-20
Two questions.

1. How can i hide the extensions of the files?
2. I always have to right click the file to play it with VLC. Any way to permanently assign the extention to vlc?

i am using 9.04

---

### Post by neon100 on 2009-10-24
was my question so difficult to  answer? doesn't anybody here know how to permanently change the Openwith option? or file the known extension types?

please?

---

### Post by herbertportillo on 2009-10-24
Right clicking on a file, going to Properties then going to the "Open With" tab and picking an application ought to do the trick. As to hiding file extensions, I don't know about that.

---

### Post by neon100 on 2009-10-25
thank you hilbert. Is there any way to permanently change the application for a certain application?

---

### Post by QLee on 2009-10-25
> **neon100 said:**
> Two questions.

1. How can i hide the extensions of the files?
2. I always have to right click the file to play it with VLC. Any way to permanently assign the extention to vlc?

i am using 9.04

GNU/Linux doesn't care about file extensions, *nix os read the file to determine what kind of file it is. The simplistic answer to your question could be to delete the file extension for any file where you don't want it to show,  ...unless you need to use it in windows.

You already have an answer for the second question.

---

### Post by neon100 on 2009-10-25
no i do not have the  answer to second question. Is there any way to PERMANENTLY change the application associated with a certain file extension? So that when i double click an mp3, it ALWAYS opens with  VLC without me right clicking it.

---

### Post by diesch on 2009-10-25
> **neon100 said:**
> no i do not have the  answer to second question. Is there any way to PERMANENTLY change the application associated with a certain file extension? So that when i double click an mp3, it ALWAYS opens with  VLC without me right clicking it.

Works for me as herbertportillo described it.

---

### Post by neon100 on 2009-10-25
> **diesch said:**
> Works for me as herbertportillo described it.

Ok . its not working for me. How do i fix it?

---

### Post by mcduck on 2009-10-25
> **neon100 said:**
> Ok . its not working for me. How do i fix it?

Make sure you right-click, go to Properties, and set the application there.

Simple right-click and "Open with Other Application" will only work for that time, while doing it in Properties should set the default.

---

### Post by neon100 on 2009-10-25
> **mcduck said:**
> Make sure you right-click, go to Properties, and set the application there.

Simple right-click and "Open with Other Application" will only work for that time, while doing it in Properties should set the default.

Worked perfectly. Thank you very very much.

---

### Post by P4man on 2009-10-25
> **QLee said:**
> GNU/Linux doesn't care about file extensions, *nix os read the file to determine what kind of file it is.

Thats not (or no longer?) true. Take any video file, add .txt to its name, and nautilus will handle it as a text file :(

Worse, I have no idea for which file types it does that, and when it uses the file header and when the extension.

First thought is that nautilus looks at the extension first, and if there is none or ti doesnt know it, then looks at the file header. But that just a guess.

---

### Post by mcduck on 2009-10-25
> **P4man said:**
> Thats not (or no longer?) true. Take any video file, add .txt to its name, and nautilus will handle it as a text file :(

Worse, I have no idea for which file types it does that, and when it uses the file header and when the extension.

First thought is that nautilus looks at the extension first, and if there is none or ti doesnt know it, then looks at the file header. But that just a guess.

Actually it will quite often look at both, and complains if the file name conflicts with the file's magic number.

Still, Linux itself doesn't need the extensions for anything, most of the files have no extensions at all, and even if you remove extension from a file the file is usually still recognized correctly. You can also try that with the "file" command.

---

