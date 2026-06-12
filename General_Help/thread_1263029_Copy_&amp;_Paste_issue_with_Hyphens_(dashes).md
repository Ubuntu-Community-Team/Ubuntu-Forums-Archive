---
title: "Copy &amp; Paste issue with Hyphens (dashes)"
date: 2009-09-10
forum: General Help
---

### Post by Rsulliv1 on 2009-09-10
Has anyone seen an issue with "soft hyphens" or hyphens?

Specifically, when a user copies text that contains a hyphen (notably from within a pdf file, but could exist in other situations) and copies it into a text editor (eclipse or gedit have been tested by me), there is an invisible space pasted into its place?

I say invisible space because when you look at a word such as:

test-me

it will be pasted as:

testme

but it will still be seven characters long. If you use arrow keys to move the cursor through the word, you'll notice that it takes two button pushes to get from the "t" to the "m".

I have seen other issues with this, but I can't seem to find out where the problem resides. Is it Adobe's issue with pdfs or ubuntu, or gnome?

I'm using Ubuntu 9.04 64-bit.

Please let me know if you have any insight, or require more definition!

---

### Post by LowSky on 2009-09-10
what happens if you paste the data to another application like openoffice word proccessor?

or use another PDF viewer?

---

### Post by StuartN on 2009-09-10
I remember bypassing this problem some years ago, but I can't remember the details - I was collating data with minus signs, continuation signs and range hyphens. I pasted the data into a non-Unicode text editor and then into my spreadsheet.

---

### Post by Rsulliv1 on 2009-09-10
StuartN, 

Which non-uni editor were you using? I used vi to test it out and it was a bit better since it actually put spaces instead of mystery chars, but still not 100%.

Low,

I tried three different editors and attached the screenshots.

Openoffice writer: showed the mystery char as a hyphen with a gray background, but it appears to be *behind* another char. It still takes two button pushes to get past it, but at least I can see it.

eclipse, doesn't show anything, but it's there.

vi, it appears as a space. I'm not sure if it's actually a ascii space or some funky char, but it appears as a space. 

So, it's happening differently in each program.


Here's a workaround: 

As you suggested, I d/l'd another pdf reader, FoxIt reader, and it was able to paste that same text into all destination programs without issue. 

Looks like it's a evince issue.

Thanks for the help and ideas guys!

---

