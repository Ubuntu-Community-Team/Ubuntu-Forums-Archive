---
title: "OpenOffice adds newlines to document"
date: 2009-11-22
forum: General Help
---

### Post by todlangweilig on 2009-11-22
When I copy and paste text from a file that came from Windows into a .doc file opened in OpenOffice and then save, close, and reopen, there are added newlines in the document. Pasting as unformatted text doesn't help. I believe this also happens in MS Office as well. Text that is typed into OpenOffice is unaffected.

I have attached a picture of what happens. This is really aggravating, is there a way to stop this? Is it something to do with the files that I'm pasting from?

```
line
line 
line
```

becomes

```
line

line

line
```

---

### Post by dandnsmith on 2009-11-22
I'm not sure, since I haven't explored this one, but:
There used to be a classic difference of representation between Unix based systems (and linux qualifies for this) and Windows/DOS based systems of the way line ends are represented. Unix used a character denoted as NL, whereas DOS used a 2 character sequence CR LF - unfortunately the CR LF shows as an extra line feed in Unix.

To get round it you have to translate from the one sequence to the other, or only paste text without line ends. Tools exist in both OS environments, but I don't know what the solution would be for you (I haven't thought about it for twenty years or so)

---

### Post by mdurham on 2009-11-22
stupid answer removed

---

### Post by todlangweilig on 2009-11-22
I just tried using dos2unix on the file that gets pasted into the document. The problem still exists.

---

### Post by mdurham on 2009-11-22
It doesn't do it on mine (I think!). Could it be some setting in your 'compatibility'? Here is a shot of mine.

---

### Post by todlangweilig on 2009-11-23
I have the same compatablity settings checked on my OpenOffice. I have attached the one of the files that cause this to happen. I hope someone can figure out whats making this happen.

here is the md5sum of the file on my side
b2d9c1635c1ad33672d093fb6de1c626

---

### Post by lisati on 2009-11-23
> **todlangweilig said:**
> I have the same compatablity settings checked on my OpenOffice. I have attached the one of the files that cause this to happen. I hope someone can figure out whats making this happen.

here is the md5sum of the file on my side
b2d9c1635c1ad33672d093fb6de1c626
I just opened up the file in Notepad on Vista - no sign of line feeds.

Edit: Wordpad formats it correctly.

---

### Post by mdurham on 2009-11-23
todlangweilig, what I did was to:
save your attached file.
open it in OOffice Word Processor
create a new empty OOffice document
cut and pasted 4 lines into the empty document
saved it as a doc file and closed it
opened it with OOffice

It was correct, with no double spacing exactly like I would have expected it to be.

Was the above procedure correct or am I misunderstanding?

Cheers, Mike

PS
I've just noticed that when I open your attached file, OOffice asks the type of paragraph break. Maybe that is something to do with it. Mine is set to LF

PPS
The file that you attached is not a .doc file

---

### Post by todlangweilig on 2009-11-23
@lisati
I've noticed that when I open my .doc file up in Windows and copy the double spaced text to wordpad, it undouble-spaces it. The file you downloaded also came from a Windows system, so Windows shouldn't have trouble opening it. 

@mdurham
I tried the method that you outlined, and it behaved normally. So I suppose your method works. However try my method and see if it causes the problem I have described.

What I have done to reproduce this problem is:
Download the attached file, Dflip.vhd.txt
Open the file in gedit
Copy the text (like the first 4 lines) to a new empty OpenOffice document
Save the document as a .doc file
Close OpenOffice
Reopen OpenOffice and the doc file
Observe the problem

Yes indeed, the file that I attached is not a .doc file, I attached the file in case there is a problem with the encoding of it. I can attach a .doc file if anyone wants one though.

---

### Post by todlangweilig on 2009-11-24
bump...Can someone try what I outline in my previous post and tell me if this happens to them as well?
Thank you.

---

### Post by todlangweilig on 2009-11-27
bump...

---

### Post by mdurham on 2009-11-27
You don't need to save as a .doc file to experience the problem, I found saving as .odt is just the same

---

### Post by todlangweilig on 2009-11-27
Hmm interesting, should I file a Bug Report then?

---

### Post by Flos Headford on 2010-04-07
[FONT="Courier New"]Micro$haft saves all text-based files with a /n (newline) indicated by a pair of ASCII characters, Cr (carriage-return,  ASCII 13 decimal) immediately followed by Lf (line-feed, ASCII 10 decimal).
Mac systems use Cr alone.
Unix-based systems use Lf alone.
MS has the historical argument that teletype printers (and later on, line-printers), often the +only+ keyboard interface to a computer, used monospaced fonts (one font per machine). In order to perform underlining or strike-outs, a printer would be sent instructions like this (and this makes more sense if you view this using something like Courier New or Monospace to render the text):-

the dog cat sat on the mat cat

then send a carriage-return (Cr), followed by

....---....................---

to give 

the *** cat sat on the mat ***

or they could send:-

the dog cat sat on the mat cat

then send a carriage-return, followed by

....___.---............---....

to give something like

the DOG *** sat on the *** cat

[Here I'm using . for a space, * for a stricken-through letter, and DOG to represent an underlined _dog_.]

It could get quite inventive, and this use of over-printing of characters actually produced the earliest instance of a "picture" being produced by a computer I ever saw. I wonder if the are any good examples left?

With the advent of the new-fangled glowing screens (even oscilloscopes were hijacked to give visual output), the need for this paper-based over-printing was consigned to the litter-bin of history.

With a teletype, you could print

it's time for
              a Kit-Kat

simply by sending

it's time for

then a line-feed (Lf) and

a Kit-Kat

(the horizontal movement of the print-head would not be affected)

When you see this double-spacing, you're using a text viewer that interprets a Cr as a newline and an Lf as a newline. That gives the double-spacing.
But it does allow you to read files which use any of the three usual conventions.

If you load a CrLf format file into the OpenOffice Word Processor, you are presented with the option to consider “CR & LF as a Paragraph break” (a newline). If you select this, the double spacing disappears. If you then “Save As”, and choose the “Open Document format” (ODF), you are asked whether you want to save in this format, or in “Text file format”. If you select ODF (“Keep Current Format”), the file is saved unchanged, with CrLf newlines; if you select “Save in ODF Format”,  each CrLf pair is converted to Lf as it is saved. This new file, when viewed in the original viewer, will appear single-spaced.

There are stand-alone utilities to perform this conversion, and vice versa.
[FONT="Courier New"][/FONT]



 [/FONT]

---

