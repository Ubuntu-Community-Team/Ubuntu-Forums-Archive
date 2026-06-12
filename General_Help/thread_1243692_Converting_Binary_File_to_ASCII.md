---
title: "Converting Binary File to ASCII"
date: 2009-08-18
forum: General Help
---

### Post by mdawg414 on 2009-08-18
I have a file (actually about 80,000 of them) which I checked out using SVN. They are HTML files that I want to do some mass searching and replacing on (ideally using sed/grep) but the problem is that they are "binary" files. Apparently when I checked them out using SVN it downloaded them in binary mode or something.

So basically, when I use "cat" to output the file, it looks fine. However, when I use "less", it warns me that the file may be a binary file. If I tell it to proceed anyways, the file appears garbled. Same thing using "vim."

At first, I thought I was just looking at junk but after looking closer, it seems that every other character is the character I am expecting to see. In between all of these characters in "vim" and "less" is a mysterious "^@" character. 

My question is, how can I convert this file to get rid of those pesky at-sign characters? The problem is, I am unable to do any grepping on these files. Is it something with "iconv"?

On a side note, just to satisfy my own curiosity, why is it that "cat" outputs the files correctly but "less" and "vim" do not?

Thanks guys!

---

### Post by HermanAB on 2009-08-18
$ man sed

Nuff sed!
;)

---

### Post by mdawg414 on 2009-08-18
Yes, I am familiar with what man pages are. Thank you.

I'm not even sure what sed can do for me, unless you were implying that I should remove the "^@" characters that way. I had tried that initally and not only did it seem a little "hacky" to me, aka, not actually converting the file, but I couldn't get sed to recognize those characters. I maybe should have been more clear, the characters "^@" aren't actually written, those just appear to be less/vim's interpretation of whatever is supposed to be there.

---

### Post by hessiess on 2009-08-18
The files are probably unicode/some other encoding. All files are `binary', as far as the computer is concerned its just a huge array of bytes.

---

### Post by jocko on 2009-08-18
If the files look ok in the cat output, why don't you try to divert the cat output to a new file?
```
cat filename > newfilename
```Or even piping the cat output to grep, sed or whatever command you wish:
```
cat filename | grep whatever
```

---

### Post by mdawg414 on 2009-08-18
Here is the output of `file $filename`

```

$ file 108656.html 
108656.html: exported SGML document text

```

When I perform 'less' on the file, the first two characters appear as <FF><FE>, any idea what that is? Hex? If I remove that first line, here is the file command

```

$ file 108656.html 
108656.html: data

```

I should also note that VIM can interpret the file correctly before I remove that first line (the one with the "<FF><FE>") but after it is removed, I see the "^@" characters all over the place. "less" has the "^@" characters all of the time.

---

### Post by mdawg414 on 2009-08-18
jocko:

Yeah that was my thought at first too, but doing that doesn't seem to change anything. When I output it to a new file, the encoding remains the same. Same story with grep, it still can't recognize patterns in the file.

Thanks for the help guys!

---

### Post by DaithiF on 2009-08-18
if it is encoding-related then check out iconv
```
man iconv
```

---

### Post by mdawg414 on 2009-08-18
I was thinking it might be iconv, but wasn't sure which encoding was being used. I looked at iconv --list but there are a lot of encodings. BTW, the encoding "specified" on the HTML page in the doctype tag is ISO-8859-1 so I have been playing around with that as the "from" encoding in iconv. No luck though

---

### Post by DaithiF on 2009-08-18
try unicode:
```
iconv -f unicode -t ascii yourfile
```

---

### Post by mdawg414 on 2009-08-18
Aha! That did the trick. It even let me figure out why it was in unicode in the first place which was nice. I ran iconv with the standard t/f options and got an invalid character sequence. Apparently, whoever generated these pages put some weird arrow character and it caused all of the documents to be in unicode.

Thanks for your help guys!

Out of curiosity, why is cat able to detect the unicode but less not? Just a fallacy in less or what?

---

