---
title: "wget, grep, regular expressions"
date: 2011-12-10
forum: General Help
---

### Post by pengyou on 2011-12-10
So** I need to get all my jpg's off of Myspace** so I can close my account.
I have had a great deal of difficulty **using wget** properly to find all the jpgs.

It seems wget should be able to do so, from what I gather, using the -r option.
I have tried Greasemonkey with a wget making script, to no avail.

I tell you this because **I have now resolved to search the page's source using grep**, **because it** **contains the links I want, and then wget those.**

Unfortunately I've no clue how to craft **a regular expression to find all lines beginning with the string "http" and ending with ".jpg"**
Can someone either tell me, or point me in the right direction so I can find out?

---

### Post by r.stiltskin on 2011-12-10
Try ^http.*\.jpg$

---

### Post by Lars Noodén on 2011-12-10
[s]You can also use [lynx --dump](http://manpages.ubuntu.com/manpages/precise/en/man1/lynx.1.html) to extract links from a page.  The links will be listed in order at the bottom of the output.[/s]

Never mind.  You're not going after the links any more.

---

### Post by Lars Noodén on 2011-12-10
You can make the pages easier to work with using [tidy](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tidy.1.html).

```

find . -name '*.html' -exec tidy -m -asxml {} \;

```

For extracting the JPEG URLs, I would recommend an HTML parser like Perl's [HTML:: Parser](http://packages.ubuntu.com/oneiric/libhtml-parser-perl)

---

### Post by Lars Noodén on 2011-12-10
> **pengyou said:**
> Unfortunately I've no clue how to craft **a regular expression to find all lines beginning with the string "http" and ending with ".jpg"**
Can someone either tell me, or point me in the right direction so I can find out?

If Myspace uses only the [img](http://www.w3.org/TR/html4/struct/objects.html#edef-IMG) elements, then you can use the package [HTML::TokeParser](apt://libxml-tokeparser-perl) to extract all the image links.  This assumes that you used [font=Courier New]--convert-links[/font] when downloading the files using [wget](http://manpages.ubuntu.com/manpages/oneiric/en/man1/wget.1.html)

```

#!/usr/bin/perl

use HTML::TokeParser;
use strict;
use warnings;

my $p = HTML::TokeParser->new(shift||"index.html");

while (my $token = $p->get_tag("img")) {
   my $img = $token->[1]{src} || "-";
   print "$img\n";
}

```

It is based on an example in the manual page for [HTML::TokeParser](http://manpages.ubuntu.com/manpages/oneiric/en/man3/HTML::TokeParser.3pm.html).  The name of the file is passed as an argument at run time.

If the script is called 'images.pl'

```

find . -name '*.html' -exec ./images.pl "{}" \;

```

---

### Post by pengyou on 2011-12-10
Oh, you perl users hurt me for my lack of perl knowledge...
This lynx thing looks interesting though.


> Try ^http.*\.jpg$     : ( Unfortunately this did not work. This is an excellent example of a regular expression, though, am I right? The problem with it (I think) is that it assumes the lines all start with http and end in .jpg, and they don't.

The problem is I have a **giant block of text containing the links** and I need to **extract them and discard the rest**. **These links follow a pattern beginning with a very specific path, **which is followed by a long string of gibberish, and then **end with a file having the extension ".jpg".** It seems to be some sort of CSS or some such thing. **And the carriage returns are not regular at all.** Or even existent, it seems...
It looks like I will need to write a python/c++ script to do it (currently good at those). It seems simple enough, I just thought there might be an easy way to search and extract via grep.

---

### Post by Vaphell on 2011-12-10
try ```
grep -Po 'http:.*?[.]jpg'
```
-P = perl flavor of regexp
-o = print only matching part

```
$ echo $'http://stuff1.xxx/1.jpg   garbage="http://stuff1.xxx/1a.jpg"\nmore garbage http://stuff1.xxx/33.jpg xyz'
http://stuff1.xxx/1.jpg   garbage="http://stuff1.xxx/1a.jpg"
more garbage http://stuff1.xxx/33.jpg xyz

$ echo $'http://stuff1.xxx/1.jpg   garbage="http://stuff1.xxx/1a.jpg"\nmore garbage http://stuff1.xxx/33.jpg xyz' | grep -Po 'http:.*?[.]jpg'
http://stuff1.xxx/1.jpg
http://stuff1.xxx/1a.jpg
http://stuff1.xxx/33.jpg

```

---

### Post by pengyou on 2011-12-10
> **Vaphell said:**
> 
try 
```
grep -Po 'http:.*?[.]jpg'
```-P = perl flavor of regexp
-o = print only matching part


Oy!
**This is fantastic**, it spit out a bunch of garbage, but **the majority of it are the links I want.**
I modified it slightly:
```

grep -Po 'http://a.*?[.]jpg'

```and it spit out even less garbage!

Now if only I could read it...
(The regex, that is) ;)
I think I got it though...

So I wrote out a whole python script anyway, which doesn't even work...

```

import sys
def main():
    file=open(sys.argv[1],'r')
    lines=[]
    look(file, sys.argv[2], sys.argv[3], lines)
    for l in lines:
        print l

def look(f, startstr, endstr, results):
    for l in f:
        start = l.find(startstr)
        end = l.find(endstr)
        if (start != -1) and (end != -1):
            end=end+len(endstr)
            results.append(l[start:end])
    
if __name__ == "__main__":
    main()

```It works on a test file, but fails when called with the source like this:
```

python script.py source http://a jpg

```**Outputs about 3 lines,** whereas** the grep solution gives many, many more** than that.
I bet I could call this on the output of grep to remove the small bit of garbage.
EDIT: Nope : /

**If anyone has anything to say about that, I would be even more grateful, otherwise, solved! **:D

---

### Post by Lars Noodén on 2011-12-10
> **pengyou said:**
> Oh, you perl users hurt me for my lack of perl knowledge...


You can cut and paste the script in post #5 without perl knowledge.  It will extract the URLs for all images in a file. When combined with [font=Courier New]find[/font] it can extract the images from a group of files.

---

### Post by pengyou on 2011-12-10
> **Lars Noodén said:**
> You can cut and paste the script in post #5 without perl knowledge.  It will extract the URLs for all images in a file. When combined with [FONT=Courier New]find[/FONT] it can extract the images from a group of files.

I'm sorry, I didn't mean to be rude...
It's just:
> 
  This assumes that you used [FONT=Courier New]--convert-links[/FONT] when downloading the files using [wget]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/wget.1.html")

**I hadn't even used wget at that point.** I just used firefox to "view source" and copypasted it into a file.

---

### Post by pengyou on 2011-12-10
Oh,** false alarm.**
My initial retrieval of **the source **via firefox **didn't contain all of the links I wanted.**
I need 49 images, and apparently the source only contained ~15.

So now** I'm back to square one.**
**How can I follow all the links in my Myspace album to get the pictures?**
: (
I have to **follow the links and then get the jpgs from those links** (I think).
I thought that was was what wget -r was for, and assumed -r stood for recursive.

Time to revisit #3, I suppose.

---

### Post by Lars Noodén on 2011-12-10
No worries.  It's just that the 8-line perl script works perfectly for extracting images -- despite being in perl. ;)

Download one web page and give it a try.  

```

wget --convert-links http://myspace.com/some/url

```

If the script's not doing what you needed we can find something else.  Building a regex for grep to go after HTML is a little risky because of all the bad HTML out there and the way lines can break.  It's safest to use a parser designed for the task.

---

### Post by Lars Noodén on 2011-12-10
> **pengyou said:**
> I thought that was was what wget -r was for, and assumed -r stood for recursive.


It should be something like this (with the long names instead):

```

wget --recursive \
     --no-host-directories \
     --convert-links \
     --no-parent \
     http://www.myspace.com/*some/url/*

```

---

### Post by pengyou on 2011-12-10
> **Lars Noodén said:**
> No worries.  It's just that the 8-line perl script works perfectly for extracting images -- despite being in perl. ;)

Download one web page and give it a try.  

```

wget --convert-links http://myspace.com/some/url

```If the script's not doing what you needed we can find something else.  Building a regex for grep to go after HTML is a little risky because of all the bad HTML out there and the way lines can break.  It's safest to use a parser designed for the task.

Well it extracted images but none of the ones I wanted:
> 
find . -name '*.html' -exec ./images.pl "{}" \;
[http://cms.myspacecdn.com/cms/x/11/48/DarkestHourTrailer5-hero.jpg](http://cms.myspacecdn.com/cms/x/11/48/DarkestHourTrailer5-hero.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/infobox_major.jpg](http://cms.myspacecdn.com/cms/x/11/50/infobox_major.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/infobox_121011-battleship.jpg](http://cms.myspacecdn.com/cms/x/11/50/infobox_121011-battleship.jpg)
[http://x.myspacecdn.com/modules/splash/static/img/fb_logo.gif](http://x.myspacecdn.com/modules/splash/static/img/fb_logo.gif)
[http://cms.myspacecdn.com/cms/x/11/40/title_music.gif](http://cms.myspacecdn.com/cms/x/11/40/title_music.gif)
[http://cms.myspacecdn.com/cms/x/11/50/music_adele.jpg](http://cms.myspacecdn.com/cms/x/11/50/music_adele.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/music_comm.jpg](http://cms.myspacecdn.com/cms/x/11/50/music_comm.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/music_kat.jpg](http://cms.myspacecdn.com/cms/x/11/50/music_kat.jpg)
[http://cms.myspacecdn.com/cms/x/11/41/title_whatshot.gif](http://cms.myspacecdn.com/cms/x/11/41/title_whatshot.gif)
[http://cms.myspacecdn.com/cms/x/11/50/121011-Expecting.jpg](http://cms.myspacecdn.com/cms/x/11/50/121011-Expecting.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/121011-Batman.jpg](http://cms.myspacecdn.com/cms/x/11/50/121011-Batman.jpg)
[http://cms.myspacecdn.com/cms/x/11/50/121011-Sherlock.jpg](http://cms.myspacecdn.com/cms/x/11/50/121011-Sherlock.jpg)
[http://cms.myspacecdn.com/cms/x/11/40/title_mv4.gif](http://cms.myspacecdn.com/cms/x/11/40/title_mv4.gif)
[http://cms.myspacecdn.com/cms/x/11/50/Avicii-Levels-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/Avicii-Levels-309x78.png)
[http://cms.myspacecdn.com/cms/x/11/50/Karmin-CrashingYourParty-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/Karmin-CrashingYourParty-309x78.png)
[http://cms.myspacecdn.com/cms/x/11/50/Gaga-MarryNight-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/Gaga-MarryNight-309x78.png)
[http://cms.myspacecdn.com/cms/x/11/50/Coldplay-CharlieBrown-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/Coldplay-CharlieBrown-309x78.png)
[http://cms.myspacecdn.com/cms/x/11/50/CJHilton-ColdSummer-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/CJHilton-ColdSummer-309x78.png)
[http://cms.myspacecdn.com/cms/x/11/50/Shakira-Loca-309x78.png](http://cms.myspacecdn.com/cms/x/11/50/Shakira-Loca-309x78.png)
[http://b.scorecardresearch.com/p?c1=2&c2=4000002&cv=2.0&cj=1](http://b.scorecardresearch.com/p?c1=2&c2=4000002&cv=2.0&cj=1)
I have to stop now, my brain is full of fog from a poor (but delicious) breakfast.
...
But I will be back later.

---

### Post by Lars Noodén on 2011-12-13
Any luck in downloading the images you are after?

---

