---
title: "Help with regular expressions?"
date: 2010-11-30
forum: General Help
---

### Post by clevertomato on 2010-11-30
I'm trying to learn regular expressions, but it's making my brain hurt. In the meantime, i have something I need to get accomplished. I need (using Bluefish regex search and replace) to find all occurrences of "http://x45.some-domain.net/path/to/graphic/filename.jpg" and replace them with "./filename.jpg". I also need to do the same for gif files.

Can someone help me by giving me a regular expression that will do this, please?

---

### Post by Brandon Williams on 2010-12-01
I'm not sure about bluefish, but in standard regex, searching for this:```
http://x45\.[^"]*/
``` and replacing it with this:```
./
``` would do the trick. The '*' is greedy, which means that it will consume as many characters as possible, so telling it to consume any character except '"' will prevent it from going past the end of a single double-quoted string.

---

### Post by clevertomato on 2010-12-02
Thanks, Brandon. That got me very close, but not quite all the way. (It essentially matches what I want, but I can't figure out how to tell it to replace the part to the left of the last "/" while KEEPING the filename.jpg to the right of the last "/".) I  tried reading more tutorials and experimenting to tweak it, but I  haven't been able to refine it just exactly for what I need. Maybe you  (or someone else) can help me refine it. Here's [hopefully] a better  description of what I need...

I'm searching for references in an HTML file that have image sources. I  want to change whatever the image source is to a relative path instead  of a URL beginning with http. So, for example:

I want
```
<img src="http://xyz.zoo.net/elephant.jpg">
```changed to
```
<img src="./elephant.jpg">
```I want
```
 <img src="http://87u2.furniture5.com/table.png">
```changed to
```
<img src="./table.png">
```I want
```
<img src="http://yoyo.electronics.net/dvdPlayer25.jpg">
```changed to
```
<img src="./dvdPlayer25.jpg">
```Any help is much appreciated. I've taught myself a lot of things, but these regular expressions are really making my head spin.

---

### Post by mendhak on 2010-12-02
Try this then:

http://[^"]*/

That's [http://,](http://,) followed by "anything but a double quote" zero or more times, until you get to a slash.

---

### Post by clevertomato on 2010-12-03
mendhak: That's actually one of the tweaks I tried before my previous message. The problem with that is it matches every link to anywhere in the html file, not just graphics files.

I thought of a work around, though, for this time. Since it's an html file, I have the benefit of there being html code that signals an image URL coming up... <img src="http://blahblahblah...    So I was able to get it to work by searching for:```
img src="http://[^"]*/
``` and replacing it with```
img src="./
```However, I would still like to figure out how to use substitution to do this, i.e. search for [FONT=Courier New]http://,[/FONT] followed by anything ending with a [FONT=Courier New].jpg[/FONT] or [FONT=Courier New].JPG[/FONT]. Then, replace that with a dot slash followed by whatever you found between the last slash and the [FONT=Courier New].jpg[/FONT] or [FONT=Courier New].JPG[/FONT].

Isn't there a way to do that using something like $1 $2 $3 in the replace portion?

---

### Post by asmoore82 on 2010-12-03
The level of support for regular expression syntax varies by the exact tool that you are using.

Historical, `sed` and `grep` and probably most other GNU tools use simplified regular expressions that need extra backslash escaping for more advanced constructs. You can get `grep` to use "extended regular expression" rules with the `-E` switch or by calling it as `egrep`. For `sed`, you have to use the `-r` switch.

I wouldn't bother with adding "./" because these are functionally identical:
```
<img src="image.jpg">
``````
<img src="./image.jpg">
```^the latter just wastes 2 bytes of space and looks more confusing to my eyes.

Without further ado, these are functionally identical:
without `-r`: ```
sed 's/src="http:\/\/\([^\/"]*\/\)*\([^"]*.jpg\)/src="\2/gI'
```
with `-r`: ```
sed -r 's/src="http:\/\/([^\/"]*\/)*([^"]*.jpg)/src="\2/gI'
```

---

### Post by asmoore82 on 2010-12-03
Here's a test where I step up through the regex,
the test string is intentionally convoluted:
```
<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />
```

Testing:
```
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />'
<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o '**[COLOR="Purple"][^/]*[/COLOR]**'
[COLOR="Red"]<img src="http:
some.server.com
some
long
path
12
11
some-image.with_strange-name.jPg" 
>[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o '[^/]***[COLOR="Purple"]/[/COLOR]**'
[COLOR="Red"]<img src="http:/
/
some.server.com/
some/
long/
path/
12/
11/
some-image.with_strange-name.jPg" /[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o '[^/**[COLOR="Purple"]"[/COLOR]**]*/'
[COLOR="Red"]http:/
/
some.server.com/
some/
long/
path/
12/
11/
 /[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o '**[COLOR="Purple"]([/COLOR]**[^/"]*/**[COLOR="Purple"])*[/COLOR]**'
[COLOR="Red"]http://some.server.com/some/long/path/12/11/
 /[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o '**[COLOR="Purple"]src="http://[/COLOR]**([^/"]*/)*'
[COLOR="Red"]src="http://some.server.com/some/long/path/12/11/[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o 'src="http://([^/"]*/)*[COLOR="Purple"]**[^"]*.jpg**[/COLOR]'
[COLOR="Red"]src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg[/COLOR]
**$** echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    egrep -i -o 'src="http://([^/"]*/)*[COLOR="Purple"]**(**[/COLOR][^"]*.jpg[COLOR="Purple"]**)**[/COLOR]'
[COLOR="Red"]src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg[/COLOR]

```
^that last set of parenthesis is only there to capture the back reference to the filename

Now to use this built up regex in `sed`, we just have to
*remember to use `-r` switch for "extended" regex
*backslash escape all of the slashes
*use the "I" option at the end for case insensitivity

```
$ echo '<img src="http://some.server.com/some/long/path/12/11/some-image.with_strange-name.jPg" />' |
    sed -r 's/src="http:\/\/([^\/"]*\/)*([^"]*.jpg)/src="\2/gI'
[COLOR="Red"]<img src="some-image.with_strange-name.jPg" />[/COLOR]
```

---

### Post by clevertomato on 2010-12-05
asmoore82: Thank you! Here's what worked in Bluefish for exactly what I wanted ... The search and replace dialog window is represented in ascii here to save uploading a screenshot. (I added the images subfolder instead of ./):

```
*************************************************************
*               *****************************************   *
* Search for:   * src="http:\/\/([^\/"]*\/)*([^"]*.jpg) *   *
*               *****************************************   *
*               *****************************************   *
* Replace with: * src="./images/\2                      *   *
*               *****************************************   *
* Scope:          Entire document                           *
*                                                           *
* Options                                                   *
*  Match Pattern: POSIX style regular expression            *
*  Replace Type : Normal                                    *
*                                                           *
*  ( ) Allow overlapping matches                            *
*  ( ) Case sensitive matching                              *
*  ( ) Pattern contains escape-sequences                    *
*  ( ) Select matches                                       *
*  ( ) Bookmark matches                                     *
*                                                           *
*  < Close >  < Replace All >  < Replace >  < Find >        *
*************************************************************

```I don't know enough about POSIX versus PERL regular expressions to know the difference. Bluefish has both options. I tried your variations using both. I also was checking "contains escape-sequences" before because I thought every \ was an escape-sequence. I still have a lot to learn about regular expressions. Finally, when I stumbled across the above settings in Bluefish, it worked!

Thanks, asmoore82 and to everyone else who contributed. I never would've been able to figure this one out. I don't know how anyone keeps these complex regular expressions straight in his head.

shawnboy

---

