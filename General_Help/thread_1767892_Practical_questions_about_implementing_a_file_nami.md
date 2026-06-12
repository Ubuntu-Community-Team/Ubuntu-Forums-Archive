---
title: "Practical questions about implementing a file naming convention"
date: 2011-05-26
forum: General Help
---

### Post by ClientAlive on 2011-05-26
Hi,

When I got started using this machine with Linux I didn't always pay attention to the way I named directories and files. Some of them follow the naming convention I've decided to use but some have spaces or are otherwise not right. I know I tiny bit about using the command line but was hoping to get some guidance on the best way to accomplish a few, certain steps to bring all the personal directory and file names into conformity. I'll list what I think I need to do to reach that goal:

I) Find all the files on my machine that are not in conformity with my chosen convention. The idea is to run some line of code that will build a big list for me. Not browsing through the whole system and making changes on by one.

(I keep thinking - 'wildcards and/ or regular expressions with something like the find command or something like that - just don't know enough about it to form a real, practical, useful line of code to do the job. Or is that even the right tool for the job.)

II) Separate from that batch all the directories and files that are not personal but are used by the system and eliminate them from my list. Also separate stored programs which filenames should not be changed.

III) Somehow rename the entire lot in one massive shot to follow my desired convention.


By the way, heres a description of the naming convention I want to use:

~ No spaces
~ Capitalize the first letter of every word
~ Use underscore only when absolutely necessary (that condition will pretty much always be when the captial letter beginning the next word is difficult to distinguish from the last letter of the previous word (such as a word beginning with captial I or L, etc when next to certain other letters. Occasionally, with longer file names, it is a logical consideration (such as grouping information in the name by type)).

~ One caveat is that some application names could not be changed. I don't mean things that are installed and in use but like some of the iso of Linux distros I have saved to mess with at some later date. I suppose I would reckon them like I do system files though.


Is this something I can expect to be able to do with Linux? How, specifically, would I accomplish those goals?

Thanks for taking the time to read this post. I appreciate any help.
----------------------------------

Edit: Also, is there something I can set up on this machine that will enforce my new naming convention. Something that just won't allow you to name something outside of the convention, with some flexibility (like with underscore), and that will only enforce it with certain folders and files (like personal ones that I create)??

Edit2: But then, if I'm successful in all that, I could potentially create other problems for myself as a result of renaming. Such as bookmarks that are already set.

In additon to all this I need to also remove redundant folders. This often cones up with eBooks or other media I download. It gets downloaded in whatever way the person sharing it created the directory. Sometimes they put a folder instide a folder inside a folder or they also include items I don't want at all like other text files with links in them or whatnot.

---

### Post by JKyleOKC on 2011-05-26
Here's a possible starting point for you: ```
jk@mehitabel:~$ find .|grep \ 
./Classen Alumni Bylaws-2.doc
./Documents/Getting Started with Ubuntu 10.04.pdf
./Public/pdf_gen/Foxit Reader.exe
./.mozilla/firefox/Crash Reports
./.mozilla/firefox/Crash Reports/InstallTime20101206122310
./.mozilla/firefox/Crash Reports/InstallTime20110323162424
./.mozilla/firefox/Crash Reports/InstallTime20101013121314

```There's a "space" character after that backslash in the "grep" command although you can't see it, and the list is only a small part of what I found when I ran this. You would really want to redirect the output to a file so that you can edit it.

As a general rule you probably don't need to look at anything outside of your home directory and its subdirectories, because most things in other locations won't be owned by you and probably ought not be changed. You might even want to exclude all hidden files/folders in your home directory. A bit of experimenting is in order before doing anything that would make permanent changes.

You could incorporate this into a script and use "sed" (stream editor) to make changes such as replacing the spaces with underscores. There's also a "tr" command that you could use to translate one character into another; I've not used it so can't give any good examples, but it's worth exploring...

I'm not at all sure you'll find your new convention to be convenient or comfortable; personally I find switching to uppercase to be less convenient than replacing spaces with underscores, but it's a matter of individual likes and dislikes.

Incidentally I'm amazed at how far you have progressed since we first corresponded in the forums here. Congratulations!

---

### Post by ClientAlive on 2011-05-26
> **JKyleOKC said:**
> Here's a possible starting point for you: ```
jk@mehitabel:~$ find .|grep \ 
./Classen Alumni Bylaws-2.doc
./Documents/Getting Started with Ubuntu 10.04.pdf
./Public/pdf_gen/Foxit Reader.exe
./.mozilla/firefox/Crash Reports
./.mozilla/firefox/Crash Reports/InstallTime20101206122310
./.mozilla/firefox/Crash Reports/InstallTime20110323162424
./.mozilla/firefox/Crash Reports/InstallTime20101013121314

```There's a "space" character after that backslash in the "grep" command although you can't see it, and the list is only a small part of what I found when I ran this. You would really want to redirect the output to a file so that you can edit it.

As a general rule you probably don't need to look at anything outside of your home directory and its subdirectories, because most things in other locations won't be owned by you and probably ought not be changed. You might even want to exclude all hidden files/folders in your home directory. A bit of experimenting is in order before doing anything that would make permanent changes.

You could incorporate this into a script and use "sed" (stream editor) to make changes such as replacing the spaces with underscores. There's also a "tr" command that you could use to translate one character into another; I've not used it so can't give any good examples, but it's worth exploring...

I'm not at all sure you'll find your new convention to be convenient or comfortable; personally I find switching to uppercase to be less convenient than replacing spaces with underscores, but it's a matter of individual likes and dislikes.

Incidentally I'm amazed at how far you have progressed since we first corresponded in the forums here. Congratulations!


Well thanks. I've been working hard to learn.

I didn't realize it but the next chapter in this eBook I'm reading (the one I'm in) is about regex (regular expressions). I think I'm starting to form and idea here (amazing, isn't it?).

I'm thinking some combination of piping ls output into grep and then piping grep output into mv (if mv will take standard output like that).

So the ls is to define the parameter as only the home directory. With the -R option it should include everything in it. That pipes into grep where I use regex to make it find filenames with spaces, dots, or whatever else I don't want them to have. That then pipes into mv which, if this is even possible, is given multiple directives, probably implementing regex again, to rename the files in the way I want them. When it gets to the mv stage maybe I can define my new names using . . . ? Well what I'm wondering about mv is whether I can define it's behavior rather than defining a file or directory name and having to enter names one by one. Maybe there is a better program for that (mv is a program right?).

Of course I would test each part before the pipe, individually, to make sure I'm getting the right output and then run a trial in virtual box.

Anyhoo . . . we'll see what happens. I've been playing around with it a bit but haven't really learned enough about regex or about more advanced  ways to use mv. Not even sure mv works that way. If we figure it out I'll definitely post the solution for others who may be interested. It sure would be cool to be able to do all that in one fatal swoop like that. 5 min and and a lot less work as apposed to  . . . God knows what if you had to search it all out yourself and rename things one by one.

Next up on the chopping block, if we get this figured out, is to create some script or something that enforces the naming convention and won't let you name something outside of it's parameters in the first place.

Wish me luck. Let me know if you have some good ideas.

Thanks
-----------------------------

Edit: Oh! I had to re-read your post to be reminded of what you said about sed and tr. Maybe this tr thing works more like I was talking about anyway. Thanks man.

---

### Post by JKyleOKC on 2011-05-27
Unfortunately the "mv" command doesn't take anything from stdin so it won't accept piped data. However scripting isn't all that difficult and can solve the problem easily. The trick is to use the advanced features in bash to execute a command or a pipeline, and store the result in a local environment variable. I don't know whether the book you are using has gotten to this stuff yet, though.

Here's an illustration: ```
UNAME=$( uname -s )
```This executes the uname command to retrieve the system type, and stores it in the variable UNAME.

A script can gather a list of all the files that meet your criteria, then read that list file by file into a pair of variables such as "oldname" and "newname", edit "newname" as required, and finally execute "mv $oldname $newname" to do the renaming before moving to the next file in the list. The beauty of this is that you can use "echo" instead of "mv" while developing the script, so it does not change anything but tells you exactly what it would be doing.

---

### Post by Thewhistlingwind on 2011-05-27
On that note, if your like me, your directories get stuffed with crusty files that you only need to access once a month or longer. The downloads directory is especially prone to this. 

You may want to look into automating file moving and sorting as well while your at it. (Especially if you have a consistent naming system.)

---

### Post by ClientAlive on 2011-05-29
Hey guys. Oh my God! Sorry I went mia on ya' I just moved into a new place and my internet will not be transferred until the 3rd. I'm sitting in McDonalds right now to get internet access. Pathetic isn't it?

:D

---

### Post by linuxinstalledfromhdd on 2011-05-29
I'm all about the in-and-out burger man..  Don't get me wrong. Mickey Ds is ok, but. It ain't no double double with a strawberry shake.

---

### Post by ClientAlive on 2011-05-31
> **linuxinstalledfromhdd said:**
> I'm all about the in-and-out burger man..  Don't get me wrong. Mickey Ds is ok, but. It ain't no double double with a strawberry shake.


We don't have In-N-Out where I am but we do have Burger Time, love em'.


As far as this whole file naming thing . . .  I've about thrown my hands up on the whole thing for now. Like everything else in Linux it seems I've got another 9 mos of intense, round the clock, studying ahead of me before the baby is born. Nothing is ever just simple, is it? Wow!

So I read and I practice and I get some ideas and I try them to see. My usual experience when trying new things on this machine is one of absolute, unrestrained terror. After what happened about a month ago I'm still pretty shaken.

So I think, well I thought I found a way to find files with spaces in them and get them into a list. I tried:

```

ls -R /home/* | grep -RE '^([[:alpha:]]*[[:blank:]]*[[:alpha:]]* ?)$'

```

and it seemed to bring up a list of things with spaces in them. Problem was, when I created a folder named: "blank space folder" in my home directory for a test and ran it again; that folder did not come up in the list. The first thing I thought of was maybe the info is coming from some database on the machine (like it does for locate) and it wasn't updated. I tried running:

```

ubdatedb

```

and ran the test again (the first code in this post) but to no avail.

I'm stumped. What's more, spaces in the filename is only one of a few things I need to search for. Even if I personally don't have any files named with certain, wrong, characteristics; it would be nice to develop something comprehensive that covers all possibilities of bad filenames.

So that's where I'm at I guess. "tr" did come up in the book I'm looking at (in the same section I'm reading about POSIX) but I don't think sed has. I think those are useful for a later part of what I need to do though anyway. Right now I'm just trying to figure out how to build the list. Any thoughts?

---

### Post by JKyleOKC on 2011-05-31
The locate database isn't involved at all with the "ls" command; that's a red herring.

Your regular expression looks unduly complicated to me. It appears to be defining a line that begins with any number of alpha characters, followed by any number of blanks, then any number of alphas, then a single blank, a single character of any sort, and the end of the line. What happens if you eliminate the " ?" just before the ")"?

Also, remember that "ls -R /home/*" is going to return more than just the list of file and directory names. Specifically, it will include header lines for each subdirectory! These may or may not match your regexp. Using "find /home" is more likely to create the kind of list you are looking for but the result will include full pathnames, not just the filename within each directory. This is a benefit, not a problem, because it eliminates possible ambiguities when you use the results to fill in a "mv" command.

---

### Post by ClientAlive on 2011-05-31
> **JKyleOKC said:**
> The locate database isn't involved at all with the "ls" command; that's a red herring.

Your regular expression looks unduly complicated to me. It appears to be defining a line that begins with any number of alpha characters, followed by any number of blanks, then any number of alphas, then a single blank, a single character of any sort, and the end of the line. What happens if you eliminate the " ?" just before the ")"?

Also, remember that "ls -R /home/*" is going to return more than just the list of file and directory names. Specifically, it will include header lines for each subdirectory! These may or may not match your regexp. Using "find /home" is more likely to create the kind of list you are looking for but the result will include full pathnames, not just the filename within each directory. This is a benefit, not a problem, because it eliminates possible ambiguities when you use the results to fill in a "mv" command.


If I run:

```

ls -R /home/* | grep -RE '^([[:alpha:]]*[[:blank:]]*[[:alpha:]]*)$'

```

I get (well I guess I can post this):


```




dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























dira
dirb
dirc
dird
dire
dirf
dirg
dirh
diri
dirj
dirk
dirl
dirm
dirn
diro
dirp
dirq
dirr
dirs
dirt
diru
dirv
dirw
dirx
diry
dirz



























John Schember
Unknown
William Shotts











Hack Central

Usenet



Hubble
Photos
RolledTheVan
Yar







```

All the "dir . . ." that are listed are inside a folder called "cliPlayground" that I created to practice learning code in a relatively safe environment.

And if I run:

```

ls -R /home/* | grep -RE '^([[:alpha:]]*[[:blank:]]*[[:alpha:]]* )$'

```


I merely get a new line (uname@host) with, apparently, no results.


I tried the "find /home" thing; and, of course, get the listing of the entire home directory - which is cool. I'll have to work on how to incorporate something for a more specific search later today. I have to run for now.

Thanks for the info Kyle


Jake

---

### Post by JKyleOKC on 2011-05-31
That blank in front of the ")" in your second attempt had to match, and having the "$" after the ")" meant that no other characters at all could follow the blank. That's why you got just an empty line.

I have no idea, though, how that regexp could give you the listing that it did, with all the "dir" entries that did not have a blank between alphas, or the empty lines. Perhaps the double "[[" and "]]" operators have something to do with it; I've never tried to use that specific construct. Try it with "'^([:alpha:][:alpha:]*[:blank:][:blank:]*[:alpha:]*.*)$'" instead and see what happens. This should match lines that begin with a single alpha, followed by any number of alphas (including none), followed by one blank then any number of blanks, followed by any number of alphas, followed by anything else.

However when I tried it here, what came out was a very short list with no embedded blanks, so it's a bit of a puzzle. Here's something that did work, though:```
jk@mehitabel:~$ [COLOR="Red"]find $HOME |egrep '[:alpha:]* [a-z]'[/COLOR]
/home/jk/Documents/Getting Started with Ubuntu 10.04.pdf
/home/jk/OldDatrec/1029tu/Data/Letters/English  report.RTF
/home/jk/OldDatrec/1214sk/lfw20/Letters/address list.RTF
/home/jk/OldDatrec/1001tl/Data/Letters/new intake form.RTF
/home/jk/OldDatrec/1001tl/Data/Letters/consignor addresses.RTF
/home/jk/.local/share/exaile/saved_tabs/order2..Public Domain Jazz (former Swiss Internet Radio) - Shoutcast Streaming Technology by www.init7.net.playlist
/home/jk/.cache/exaile/dynamic/Bob Howard and his Orchestra
/home/jk/.cache/exaile/dynamic/Les Brown & His Band of Renown
/home/jk/.thunderbird/zwqgku0x.default/Mail/Local Folders/word tips.msf
/home/jk/.thunderbird/zwqgku0x.default/Mail/Local Folders/word tips
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes/Trash
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes/Trash.msf
jk@mehitabel:~$ 

```Notice that only those blanks followed by a lower-case character showed up in the list.

---

### Post by ClientAlive on 2011-06-01
> **JKyleOKC said:**
> That blank in front of the ")" in your second attempt had to match, and having the "$" after the ")" meant that no other characters at all could follow the blank. That's why you got just an empty line.

I have no idea, though, how that regexp could give you the listing that it did, with all the "dir" entries that did not have a blank between alphas, or the empty lines. Perhaps the double "[[" and "]]" operators have something to do with it; I've never tried to use that specific construct. Try it with "'^([:alpha:][:alpha:]*[:blank:][:blank:]*[:alpha:]*.*)$'" instead and see what happens. This should match lines that begin with a single alpha, followed by any number of alphas (including none), followed by one blank then any number of blanks, followed by any number of alphas, followed by anything else.

However when I tried it here, what came out was a very short list with no embedded blanks, so it's a bit of a puzzle. Here's something that did work, though:```
jk@mehitabel:~$ [COLOR="Red"]find $HOME |egrep '[:alpha:]* [a-z]'[/COLOR]
/home/jk/Documents/Getting Started with Ubuntu 10.04.pdf
/home/jk/OldDatrec/1029tu/Data/Letters/English  report.RTF
/home/jk/OldDatrec/1214sk/lfw20/Letters/address list.RTF
/home/jk/OldDatrec/1001tl/Data/Letters/new intake form.RTF
/home/jk/OldDatrec/1001tl/Data/Letters/consignor addresses.RTF
/home/jk/.local/share/exaile/saved_tabs/order2..Public Domain Jazz (former Swiss Internet Radio) - Shoutcast Streaming Technology by www.init7.net.playlist
/home/jk/.cache/exaile/dynamic/Bob Howard and his Orchestra
/home/jk/.cache/exaile/dynamic/Les Brown & His Band of Renown
/home/jk/.thunderbird/zwqgku0x.default/Mail/Local Folders/word tips.msf
/home/jk/.thunderbird/zwqgku0x.default/Mail/Local Folders/word tips
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes/Trash
/home/jk/.thunderbird/zwqgku0x.default/Mail/smart mailboxes/Trash.msf
jk@mehitabel:~$ 

```Notice that only those blanks followed by a lower-case character showed up in the list.


Right on. I'll have to give that a try. Thanks.

Oh, by the way the double square brackets thing came right out of the book I'm reading. That original construction (from a couple posts ago) is almost exactly like the book with regard to formatting (I added the "*" I think) and changed what tags were in it compared to the ones he used in the book. The book I'm reading is called: "The Linux Command Line" by: William Shotts btw.

The oddness about how that list came up for me may be explained by the fact that regular expressions are somehow tied to ASCII. The following quote from that section of the book can shows what's been going into my head about it:  ;)

> 
**POSIX Character Classes**

The traditional character ranges are an easily understood and effective way to handle the problem of quickly specifying sets of characters. Unfortunately, they don’t always work. While we have not encountered any problems with our use of grep so far, we might run into problems using other programs.

Back in Chapter 5, we looked at how wildcards are used to perform pathname expansion. In that discussion, we said that character ranges could be used in a manner almost identical to the way they are used in regular expressions, but here’s the problem:

```

[me@linuxbox ~]$ ls /usr/ bin/[ABCDEFGHIJKLMNOPQRSTUVWXYZ]*
/usr/sbin/MAKEFLOPPIES
/usr/sbin/NetworkManagerDispatcher
/usr/sbin/NetworkManager

```

(Depending on the Linux distribution, we will get a different list of files, possibly an
empty list. This example is from Ubuntu) This command produces the expected result
—a list of only the files whose names begin with an uppercase letter, but:

```

[me@linuxbox ~]$ ls /usr/sbin/[A-Z]*
/usr/sbin/biosdecode
/usr/sbin/chat
/usr/sbin/chgpasswd
/usr/sbin/chpasswd
/usr/sbin/chroot
/usr/sbin/cleanup-info
/usr/sbin/complain
/usr/sbin/console-kit-daemon

```

with this command we get an entirely different result (only a partial listing of the results
is shown). Why is that? It’s a long story, but here’s the short version:

Back when Unix was first developed, it only knew about ASCII characters, and this feature reflects that fact. In ASCII, the first thirty-two characters (numbers 0-31) are control codes (things like tabs, backspaces, and carriage returns). The next thirty-two (32-63) contain printable characters, including most punctuation characters and the numerals zero through nine. The next thirty-two (numbers 64-95) contain the uppercase letters and a few more punctuation symbols. The final thirty-one (numbers 96-127) contain the lowercase letters and yet more punctuation symbols. Based on this arrangement, systems using ASCII used a collation order that looked like this:

ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz

This differs from proper dictionary order, which is like this:

aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ

As the popularity of Unix spread beyond the United States, there grew a need to support characters not found in U.S. English. The ASCII table was expanded to use a full eight bits, adding characters numbers 128-255, which accommodated many more languages. To support this ability, the POSIX standards introduced a concept called a locale, which could be adjusted to select the character set needed for a particular location. We can see the language setting of our system using this command:

```

[me@linuxbox ~]$ echo $LANG
en_US.UTF-8

```

With this setting, POSIX compliant applications will use a dictionary collation order rather than ASCII order. This explains the behavior of the commands above. A character range of [A-Z] when interpreted in dictionary order includes all of the alphabetic characters except the lowercase “a”, hence our results.

To partially work around this problem, the POSIX standard includes a number of character classes which provide useful ranges of characters. They are described in the table below:

[Quote]
**Table 20-2: POSIX - Character Classes - Character Class Description**


[:alnum:] The alphanumeric characters. In ASCII, equivalent to:
[A-Za-z0-9]

[:word:] The same as [:alnum:], with the addition of the underscore
(_) character.

[:alpha:] The alphabetic characters. In ASCII, equivalent to:
[A-Za-z]

[:blank:] Includes the space and tab characters.

[:cntrl:] The ASCII control codes. Includes the ASCII characters zero
through thirty-one and 127.

[:digit:] The numerals zero through nine.

[:graph:] The visible characters. In ASCII, it includes characters 33
through 126.

[:lower:] The lowercase letters.

[:punct:] The punctuation characters. In ASCII, equivalent to:
[-!"#$%&'()*+,./:;<=>?@[\\\]_`{|}~]

[:print:] The printable characters. All the characters in [:graph:]
plus the space character.

[:space:] The whitespace characters including space, tab, carriage
return, newline, vertical tab, and form feed. In ASCII,
equivalent to:
[ \t\r\n\v\f]

[:upper:] The upper case characters.

[:xdigit:] Characters used to express hexadecimal numbers. In ASCII,
equivalent to:
[0-9A-Fa-f]


Even with the character classes, there is still no convenient way to express partial ranges, such as [A-M].

Using character classes, we can repeat our directory listing and see an improved result:

```

[me@linuxbox ~]$ ls /usr/sbin/[[:upper:]]*
/usr/sbin/MAKEFLOPPIES
/usr/sbin/NetworkManagerDispatcher
/usr/sbin/NetworkManager

```

Remember, however, that this is not an example of a regular expression, rather it is the shell performing pathname expansion. We show it here because POSIX character classes can be used for both.
[/Quote]

---

### Post by JKyleOKC on 2011-06-01
I first thought that those examples from the book would return any file whose name contained an uppercase character, even if it was not the first, but later realized that they were using "ls" and "shell globbing" to make the point. Had they been using grep, absence of the initial "^" character would have made my first impression correct!

I do have a copy of that book on my main machine for reference; you can find the instructions about "sed" starting at page 295 or so (if you have the same edition I have here). However there's no need to get too involved with sed until you have the system generating the file list you want to work with!

---

### Post by ClientAlive on 2011-06-03
> **JKyleOKC said:**
> I first thought that those examples from the book would return any file whose name contained an uppercase character, even if it was not the first, but later realized that they were using "ls" and "shell globbing" to make the point. Had they been using grep, absence of the initial "^" character would have made my first impression correct!

I do have a copy of that book on my main machine for reference; you can find the instructions about "sed" starting at page 295 or so (if you have the same edition I have here). However there's no need to get too involved with sed until you have the system generating the file list you want to work with!


Right on. Well I guess I underestimated what it would take to do something like this. Of course there is probably some gui app out there that does it for me (might even be something already on here from the standard install). I won't learn much by using something like that though. Guess I'll just keep plugging away. Sooner or later there has to come a day when these things are easy for me.

Got my internet though, so that's cool.

Have a great weekend Kyle.

---

### Post by nothingspecial on 2011-06-05
[COLOR="Red"][SIZE="3"]DO NOT TYPE THESE COMMANDS IN YOUR HOME DIRECTORY[/SIZE][/COLOR]

They are examples to get you started. If you did them from your home, stuff would break because they will rename files that your system expects to start with lowercase letters and have spaces. Mess about with them in a test directory.

As a starting point for a different way of doing this, consider using a for loop with find, rather than ls.
```

$touch blah "blah blag" "look spaces cool" blag Banana "Apples and Pears"
$ls
Apples and Pears  Banana  blag  blah  blah blag  look spaces cool
$for f in $(find . -type f); do g=$(echo "$f" | sed -e 's/\<./\U&/g'); mv "$f" "$g";done
mv: `./Banana' and `./Banana' are the same file
$ls
Apples And Pears  Banana  Blag  Blah  Blah Blag  Look Spaces Cool
$for f in $(find . -type f); do g=$(echo "$f" | sed -e 's/ /_/g'); mv "$f" "$g" 2> /dev/null; done
$ls
Apples_And_Pears  Banana  Blag  Blah  Blah_Blag  Look_Spaces_Cool
$
```

The first bit of the first command assigns the results of <find . -type f> to the variable $f. That find command will find every file in every directory from where you type it down. This is why it is so dangerous - [COLOR="Red"]be very, very careful with find[/COLOR] 

The second bit feeds $f (the results of find) into sed which capitalises the first letter of each word and assigns the reults to the variable $g.

The last bit renames $f (the results of find) to $g (the results of using sed on the files find found).

The second command does exactly the same thing except that sed changes spaces to underscores.

You can see that mv spat out an error in the first command because "Bananas" was already capitalised. This is not a problem but to eliminate the errors I put 2> /dev/null in the second command. That just sends errors to a special file "/dev/null" which is like a rubbish bin. It is a black hole. If you send stuff there it disappears ([COLOR="Red"]again be careful sending stuff to /dev/null[/COLOR])

---

### Post by ClientAlive on 2011-06-06
> **nothingspecial said:**
> [COLOR="Red"][SIZE="3"]DO NOT TYPE THESE COMMANDS IN YOUR HOME DIRECTORY[/SIZE][/COLOR]

They are examples to get you started. If you did them from your home, stuff would break because they will rename files that your system expects to start with lowercase letters and have spaces. Mess about with them in a test directory.

As a starting point for a different way of doing this, consider using a for loop with find, rather than ls.
```

$touch blah "blah blag" "look spaces cool" blag Banana "Apples and Pears"
$ls
Apples and Pears  Banana  blag  blah  blah blag  look spaces cool
$for f in $(find . -type f); do g=$(echo "$f" | sed -e 's/\<./\U&/g'); mv "$f" "$g";done
mv: `./Banana' and `./Banana' are the same file
$ls
Apples And Pears  Banana  Blag  Blah  Blah Blag  Look Spaces Cool
$for f in $(find . -type f); do g=$(echo "$f" | sed -e 's/ /_/g'); mv "$f" "$g" 2> /dev/null; done
$ls
Apples_And_Pears  Banana  Blag  Blah  Blah_Blag  Look_Spaces_Cool
$
```

The first bit of the first command assigns the results of <find . -type f> to the variable $f. That find command will find every file in every directory from where you type it down. This is why it is so dangerous - [COLOR="Red"]be very, very careful with find[/COLOR] 

The second bit feeds $f (the results of find) into sed which capitalises the first letter of each word and assigns the reults to the variable $g.

The last bit renames $f (the results of find) to $g (the results of using sed on the files find found).

The second command does exactly the same thing except that sed changes spaces to underscores.

You can see that mv spat out an error in the first command because "Bananas" was already capitalised. This is not a problem but to eliminate the errors I put 2> /dev/null in the second command. That just sends errors to a special file "/dev/null" which is like a rubbish bin. It is a black hole. If you send stuff there it disappears ([COLOR="Red"]again be careful sending stuff to /dev/null[/COLOR])


Oh My God!! Where did you learn all this stuff man?! Holy Cow!

I just saw this and it's super late and I'm soooo tired. I'll have to really take a look at this after work tomorrow. I'm excited though!

Thanks nothingspecial.

   :D

---

### Post by ClientAlive on 2011-06-06
Well, I'm gonna mark this one as solved for now. Maybe I can dig in and learn to understand what all that means and make some good use out of it.


Thanks again.

:D

---

