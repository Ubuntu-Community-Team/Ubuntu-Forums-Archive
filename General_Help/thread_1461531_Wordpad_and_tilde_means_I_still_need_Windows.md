---
title: "Wordpad and tilde means I still need Windows"
date: 2010-04-24
forum: General Help
---

### Post by malleeblue on 2010-04-24
I converted to Ubuntu from Windows almost 2 years ago and couldn't be happier, however there are 2 little things which keep taking me back to Windows.
[LIST=1]
[*]Wordpad
[*]Finding and deleting files ending in tilde
[/LIST]

_WORDPAD_
Each week I get sent a few files in .rtf format which I edit and upload to the Internet. They are originally created in Word and so are over 100kb each, but after I'm done with them in Wordpad they're down to just 2kb with formatting retained (all I do is remove about 20 lines of text). So far in my search for a Linux 'Wordpad' I've not found one that keeps the formatting but shrinks it this well. So that's one reason why I need to return to my former OS.

_TILDE_
This one only came up today and after searching and searching the Internet for a solution I just couldn't find one. I cannot figure out how to do a search just for files ending in tilde (~). And then after that, I'm not sure how I would go about bulk-deleting only those files. So I booted into Windows and viola, I was instantly on my way to finding and then deleting*.

So does anyone have any solution(s) to my issues?

* [SIZE="1"]For those who won't be able to resist asking why I want to delete files ending in tilde (~), it's because I want to take a backup of a backup and I don't want or need those files in the 2nd backup.[/SIZE]

---

### Post by P4man on 2010-04-24
About wordpad; I think it saves in compressed RTF by default. I have no idea of a linux editor that does that, but Ive got to wonder.. why? compress it with 7zip or any other utility that your windows collegues can handle, and they will be as small, if not smaller than the wordpad document.

Another "solution" that may make some cringe, but its is just to run wordpad under ubuntu. It should work without issues using wine. Certainly less hassle than dual booting.

As for the tilde, I dont see the problem. I just tried, places > search for files, and I entered

```
*~
```

Comes up with a list of files that end in ~
(and I can just select and delete them if I want).

---

### Post by malleeblue on 2010-04-24
Thanks P4man for your suggestions. The zip one is good but the person sending me the file is 'challenged' re computers and I wouldn't waste my time. Regarding the *~, I tried that and other options but no files were returned in my list, and I know there are plenty of them. Would it have anything to do with me trying to do this search on an external USB HDD? I have selected it properly from the list.

---

### Post by HermanAB on 2010-04-24
Howdy,

Why even bother searching first?

Just blow them away directly:
$ cd /media/whatever
$ rm *~

OOo and Abiword can both edit RTF files.

---

### Post by P4man on 2010-04-24
Small addendum: to see those files you do have to click on "select more options"  and then select "**show hidden and backup files**". Since files ending with ~ are backup files. Should have mentioned that earlier, but I always have that option on, so I forgot :)

---

### Post by malleeblue on 2010-04-24
@HermanAB, I wanted to search before performing rm just to feel more sure about what I was doing. And re OOo and Abi, yes I know they can edit but they can't get the size down like Wordpad does.


@P4man, thank you for the update, that was what I hadn't done. Very much appreciated.

---

### Post by P4man on 2010-04-24
> **HermanAB said:**
> Howdy,

OOo and Abiword can both edit RTF files.

OO doesnt write as compressed RTF though. 
Not sure about abiword

---

### Post by Gillingham on 2010-04-24
Out of interest have you tried running wordpad using wine?

David

---

### Post by srs5694 on 2010-04-24
To delete all files in a directory that end in a tilde (~), try this at the command line:

```

rm `find ./ -name "*~"`

```

Note that those are back-ticks (`) around the find command, not single quotes ('). You must be in the directory specified for this to work. You could easily convert it to a script, if you wanted to have something you could double-click to work, but you'd need a way to enter the directory to be cleaned of those files. (Or you'd need to hard-code a directory, such as your home directory.)

As to RTF files, most word processors can produce them, but I can't say I've studied which ones produce RTF files with the smallest size. If nothing else, Gillingham's suggestion of running WordPad in WINE would almost certainly work, but I suspect you could find somehing that would work as well in Linux. Try running Synaptic and searching for "RTF". When I do this, I find a bunch of hits, including editors, libraries, and specialized utilities.

---

### Post by fragos on 2010-04-24
There is an RTF editor "Ted" which is fast with a limited function set like WordPad. I don't however know if it deals directly with the compressed RTF files mentioned. I've never run into those that I'm aware of.

---

### Post by malleeblue on 2010-04-24
> **Gillingham said:**
> Out of interest have you tried running wordpad using wine?

David

Yes, but with my newbieness I've not been able to get it to work.


> **fragos said:**
> There is an RTF editor "Ted" which is fast with a limited function set like WordPad. I don't however know if it deals directly with the compressed RTF files mentioned. I've never run into those that I'm aware of.

I've tried Ted in the past but it doesn't compress like Wordpad.

---

### Post by donsy on 2010-04-24
I have wine1.2 installed and it already includes Wordpad. In the Applications > Wine menu, if I choose Browse C: Drive, then open the windows folder, and then the system32 folder it's there and I can execute it.

---

### Post by malleeblue on 2010-04-24
> **donsy said:**
> I have wine1.2 installed and it already includes Wordpad. In the Applications > Wine menu, if I choose Browse C: Drive, then open the windows folder, and then the system32 folder it's there and I can execute it.

Thanks Donsy. I upgraded to wine1.2 after reading your post and was happy to find Wordpad just as you said. Interestingly, it shrunk a test file just like it's in-Windows relative but with a small difference in final size -- from 170K to 1.5K in Windows, and from 170K to 3.3K in wine's Wordpad. It's close enough for me though!   *[SIZE="1"]*malleeblue waves as Windows floats off into the distance*[/SIZE]*

I love this forum!! You guys are great, thank you!

---

