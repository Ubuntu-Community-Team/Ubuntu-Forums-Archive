---
title: "ascii codes in gedit"
date: 2011-06-14
forum: General Help
---

### Post by linux_trojan on 2011-06-14
I am writing a program in Gambas to send output to an ASCII file.  The ASCII file will then be opened by gedit.  I was wondering if it is possible to insert some ASCII code in the ASCII file that will cause gedit to do stuff like FORM FEED?  Stuff like Bold, Carriage Control, etc would be good too.  How would that ASCII code look?

---

### Post by kalaharix on 2011-06-14
Hi

The process is the same as with most programming languages. Gambas documentation gives a list of ASCII codes [http://gambasdoc.org/help/def/ascii?show](http://gambasdoc.org/help/def/ascii?show).

The answer to your question would therefore be something like:
"hello " & Chr(10) & "there" & Chr(12) & "This is a new page"

However you would have to load the resulting file into a wordprocessing application like OpenOffice or Abiword to see the correct result. Gedit is a text file application and does not interpret page feeds.

---

### Post by HermanAB on 2011-06-14
RTF or HTML.

---

### Post by linux_trojan on 2011-06-14
Oh thats why it didnt work in gedit.  I was thinking about using HTML.  Now that I know this works, I will trying it in a *.doc.  Only problem is that Open Office repositions the text, doesnt leave it like it is in ASCII.  So I guess I will have to give more ASCII commands to tell Open Office where to place the text.  But at least this way I can add italics and bold and stuff.  Isnt there a font in Open Office that reads text like ASCII?  Courier or something?

---

### Post by cipherboy_loc on 2011-06-14
Yes, Courier will work or Liberation Mono. These are fonts from the monospace family, as each printable character gets the same amount of space (including the space character).

---

