---
title: "build index.html into a full html page"
date: 2010-03-09
forum: General Help
---

### Post by tanha on 2010-03-09
Hello,

I used wget -r to get all the web pages that were linked from index.html. The pages listed in index.html are all chapters. After using wget -r, all the chapters are now in the same folder on my local hard drive. Is there a way to build the chapters in their proper order into a "long"/"full" web page, rather than simply having each chapter as a link/next link on a previous page?

Thank you,
t

---

### Post by darolu on 2010-03-09
You can always manually edit the index.html file, copying the content between <body></body> tags.
I recently installed Bluefish 2, it is pretty neat, has a new wrapping feature that helps a lot with large files.

---

### Post by tanha on 2010-03-09
> **darolu said:**
> You can always manually edit the index.html file, copying the content between <body></body> tags.
I recently installed Bluefish 2, it is pretty neat, has a new wrapping feature that helps a lot with large files.

I was hoping for something a automated, as there are a lot of files... any ideas? Basically concatenating the files and appending one after the other.

---

### Post by darolu on 2010-03-09
The problem with concatenating is it will include doctype, head, title, etc... tags, and it may not work right, not to mention it won't be precisely w3.org compliant.

You can do it with:
```
$ cat file1.html file2.html file3.html > newfile.html
```

---

### Post by tanha on 2010-03-09
> **darolu said:**
> The problem with concatenating is it will include doctype, head, title, etc... tags, and it may not work right, not to mention it won't be precisely w3.org compliant.

You can do it with:
```
$ cat file1.html file2.html file3.html > newfile.html
```

The other problem is that the pages are numbered 1, 2, ... I'm hoping there is some app that can read the TOC, and then append the chapters in the correct order. Or is this something that needs to be done manually; that is, by me?

---

### Post by lakersforce on 2010-03-09
oops, misread.

---

### Post by tanha on 2010-03-09
> **lakersforce said:**
> The wget manpage tells you how-to.

I didn't see that... could you point out where it does exactly (I know that it does ''recursive downloading'' which is what I used, but I don't want the web page to look like the online one -- that's the problem)?

---

### Post by dcstar on 2010-03-09
> **tanha said:**
> The other problem is that the pages are numbered 1, 2, ... I'm hoping there is some app that can read the TOC, and then append the chapters in the correct order. Or is this something that needs to be done manually; that is, by me?

If you want to **redesign** the web site, then you must do it yourself.

There is no tool that can read your mind and create a new web site based on the files you have downloaded.

---

### Post by tanha on 2010-03-09
> **dcstar said:**
> If you want to **redesign** the web site, then you must do it yourself.

There is no tool that can read your mind and create a new web site based on the files you have downloaded.

It's not that I want it it read my mind and redesign the webpage per se. I'm just looking for an app that will read the layed out structure of the chapters and append them one after the other, creating a long webpage, (which I will then convert to PDF). So, this is looking like a "no," still?

---

### Post by |{urse on 2010-03-09
I'm guessing this is what you mean?

```

wget \
–recursive \
–no-clobber \
–page-requisites \
–html-extension \
–convert-links \
–restrict-file-names=windows \
–domains insertwebsitehere.com \
–no-parent \
www.insertwebsitehere.com/index.html

```

[http://www.techstroke.com/download-whole-website-in-linux-the-smart-way.html]("http://www.techstroke.com/download-whole-website-in-linux-the-smart-way.html")

---

### Post by darolu on 2010-03-09
This apps may help you too:
[http://iterati.org/ebookTools/vHtmlMerger/Default.aspx](http://iterati.org/ebookTools/vHtmlMerger/Default.aspx)

[http://softsnow.griffin3.com/merger/merger.shtml](http://softsnow.griffin3.com/merger/merger.shtml) (should work with wine)

---

### Post by |{urse on 2010-03-09
> **tanha said:**
> It's not that I want it it read my mind and redesign the webpage per se. I'm just looking for an app that will read the layed out structure of the chapters and append them one after the other, creating a long webpage, (which I will then convert to PDF). So, this is looking like a "no," still?

Oh nevermind I was way off there (sheer forum blindness =)
Yeah just hit crtl + u and copy paste the main page and all relevant pages into one text file. So far as the doctypes and all that there shouldn't be any major probs there.

---

### Post by tanha on 2010-03-09
> **|{urse said:**
> I'm guessing this is what you mean?

```

wget \
–recursive \
–no-clobber \
–page-requisites \
–html-extension \
–convert-links \
–restrict-file-names=windows \
–domains insertwebsitehere.com \
–no-parent \
www.insertwebsitehere.com/index.html

```

[http://www.techstroke.com/download-whole-website-in-linux-the-smart-way.html]("http://www.techstroke.com/download-whole-website-in-linux-the-smart-way.html")

That seems like the right idea, thank you; although it did the same as before, hmmm... did i do it wrong?

Here is what I used:

```
wget --recursive --no-clobber --page-requisites --html-extension --convert-links --restrict-file-names=windows --domains=domain.org --no-parent http://.../index.html
```

It still made individual pages like the original has, instead of one "really long" web page...

---

### Post by |{urse on 2010-03-09
yeah sorry I apologized for that above =) I'm a bigmouth who doesn't carefully read the OP before posting sometimes. ;)

---

### Post by tanha on 2010-03-09
> **|{urse said:**
> yeah sorry I apologized for that above =) I'm a bigmouth who doesn't carefully read the OP before posting sometimes. ;)

np. i do the same thing lol

---

