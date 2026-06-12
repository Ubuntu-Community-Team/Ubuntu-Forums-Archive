---
title: "How does Ubuntu sort?  It doesn't  follow ascii.  This affect web pages?"
date: 2010-08-30
forum: General Help
---

### Post by finny388 on 2010-08-30
I used to name folders with an exclamation point as first character in Windows to bring them to the top when a folder list was sorted alphabetically. ([ascii]("http://www.asciitable.com/") sort)

I created such a folder as one of my folders in Yahoo Mail. ("!Ubuntu")

I noticed it was ignoring the "!" altogether and placing it between the t's and v's.

I checked my mail on a Windows machince and the folder is right at the top!

I noticed the same difference between Windows Explorer and Nautilus.

How does Ubuntu sort?
How can this affect webpages??

Thanks

---

### Post by LowSky on 2010-08-30
Ubuntu and Linux in general doesn't use the same naming conventions that Windows uses. For instance: Linux sees capital letters as different letters than lower case letters. So Widget would be a different file than widget. Also the period is used to hide folders so .widget wouldn't show up in natilus unless you allow hidden folders to be seen.
 
I don't see how this would effect a webpage. Viewing webpages is based on the borwser. Otherwise location of where it appears on a file list isn't going to effect the use or availibility.

---

### Post by finny388 on 2010-08-30
I thought it would be up to Yahoo.

I use Firefox on both boxes. So I am using different version of Firefox (FF-Ubuntu vs FF-Windows) ?

I just notices FF-Ubuntu is 3.6.9 while Windows has 3.6.8, could that be the difference?

But why wouldn't this be up to Yahoo?

---

### Post by finny388 on 2010-09-02
^

---

### Post by finny388 on 2010-09-25
Now I see Chromium sorts like Windows would with '!' sorted above 'a' as I wanted.

So it depends if the browser is using the OS's sort logic?

---

### Post by The Cog on 2010-09-25
[http://www.linux.com/archive/feed/53781](http://www.linux.com/archive/feed/53781)
is a good reference. 
In brief, the command l**ocale -a** will tell you which locales are available. The C locale is always available, You can set a locale in the command line with the command **export LC_ALL=C** or whatever locale you want. The C locale will separate upper and lower case as well as separating non-alpha characters. See this littel excercise:
> $ **export LC_ALL=**
$ **ls**
aaa  aab  Aac  +aad  aae
$ **export LC_ALL=C**
$ **ls**
+aad  Aac  aaa	aab  aae
$ **export LC_ALL=POSIX**
$ **ls**
+aad  Aac  aaa	aab  aae
$ **export LC_ALL=en_GB.utf8**
$ **ls**
aaa  aab  Aac  +aad  aae

I'm not sure where the best place is to set your preferred locale. Putting the command in ~/.bashrc is one option (need to log out and back in again afterwards).

P.S.
I think this is unlikely to be affecting web pages you visit.

---

### Post by finny388 on 2010-09-25
gee whiz, I thought ASCII was universal.
then I learn it is OS dependent
now it also locale dependent

If I am using USA locale in Windows and USA locale in Ubuntu, why would they sort differently?

> P.S.
I think this is unlikely to be affecting web pages you visit.

but it does. or do you mean locale changes won't affect browsers?

if it doesn't affect browsers then browsers' sorting is independent of how the OS sorts?
as I see it there 3 variables: OS, locale, browser
and 2 areas affected: file browsing (e.g. nautilus, ls) and web browsing (e.g firefox or chromium)  -- (I thought it would just depend on the browser but Yahoo mail folders sort differently between FF and Chromium)

It is not clear to me how each variable affects each area.

---

### Post by The Cog on 2010-09-26
ASCII is universal, apart from the fact that it has local variations. Very few things use plain ASCII any more. More common are UFT8 and ISO8859-1. All these are character encoding schemes - how characters, called glyphs, are represented by a series of bytes. "A" happens to be represented by the number 65 in all of the above schemes. And in fact, all the printable ASCII characters have the same byte value in all three encoding schemes. ISO8859-1 and UTF8 have codes for more characters than ASCII has though.

In terms of sorting text, it gets interesting. Since computer programs store text in memory by storing the byte sequences that code for those characters, the simple programs simply sort text by sorting on the values of the byte sequences. Thus "A" (65) and "a" (97) get sorted quite far apart from each other, and "[" for instance goes between upper and lower case letters.

More recently, people have started to try and sort text more in line with the natural meaning of the letters rather than the arbitrary values of the byte codings. Because these sorting expectations tend to vary by location and language etc, the idea of a locale has been introduced. Lots of software seems to use the locale settings these days.

As for web pages, I'm not sure. I can think of three possibilities:

1: The web server dishes out tables in the order that it chooses. In this case, you locale is completely irrelevant and text is shown in the sorting order that the web server chooses to use.

2: The browser tells the web server what its locale is along with the query, and the server sorts the tables in the web page that it serves accordingly. I don't know if the browser normally tells the server what its locale setting is, so I don't know if this is possible.

3: The web page contains javascript that does the sorting, on the client's PC. If this happens, it is possible (again I don't know) that the javascript sort might make use of the locale.

---

### Post by Lateralis on 2010-09-26
```

locale     # displays which locale you currently have as your default
locale -a  # displays which locales you can use

```

On my machine, LC_ALL is an empty field.  I just did a test by making a file "!hello" in my home directory.  That was placed between *h* and *i* with ls.  

You can modify which ones you use (you could try either C or POSIX) by editing the /etc/default/locales file.  

See [this randomly googled link]("http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html") and [this Ubuntu wiki page]("https://help.ubuntu.com/community/Locale").

---

### Post by finny388 on 2010-09-26
Thanks The Cog, that cleared a fair bit up for me.

I am fine with how my Ubuntu box sorts. (locale reveals UTF8, LANG=en_CA).

The riddle is
[COLOR="Blue"]FF/Ubuntu/YahooMailFolders = exclamation points sort to the bottom

FF/Windows/YahooMailFolders
Chromium/Ubuntu/YahooMailFolders = exclamation points sort to the top[/COLOR]

So I am surprised that Firefox
a)doesn't use the OS locale/scheme (or consult the webserver)
b)is not consistent across platforms

I'd consider this a flaw, if not a bug.

This is closest to option 2 (I wasn't sure if you meant the browser imposes the OS's scheme to the webserver or its own (which it appears to do in this case))


The Cog:> 
1: The web server dishes out tables in the order that it chooses. In this case, you locale is completely irrelevant and text is shown in the sorting order that the web server chooses to use.

2: The browser tells the web server what its locale is along with the query, and the server sorts the tables in the web page that it serves accordingly. I don't know if the browser normally tells the server what its locale setting is, so I don't know if this is possible.

3: The web page contains javascript that does the sorting, on the client's PC. If this happens, it is possible (again I don't know) that the javascript sort might make use of the locale.


---

### Post by The Cog on 2010-09-26
Regards to option 2: I just took a trace of firefox on Ubuntu fetching this thread, and in the request I see the line:
> Accept-Language: en-gb,en;q=0.7,en-us;q=0.3
I have no idea what the q numbers mean, but it is clear that my browser is asking for english(GB) as a preference. 

It occurs to me, I wonder if your Ubuntu firefox is asking for US english - have a look in Edit / Preferences / Content / Languages / Choose to see.

---

### Post by finny388 on 2010-09-26
Indeed, English/United States [en-us]

So I tried GB (and Canada), moved them to top preference, and restarted Firefox - no change.

Went over to see if something was different on my Windows machine. It too was en-us, and there too I tried the above with no change.

Yet they sort differently on Yahoo (I don't think this helps but in gmail they sort the same (at top)) for labels)

Darn it, I thought you nailed it there.

What is a trace and how did you do this:
> Regards to option 2: I just took a trace of firefox on Ubuntu fetching this thread, and in the request I see the line:
Quote:
Accept-Language: en-gb,en;q=0.7,en-us;q=0.3

---

### Post by The Cog on 2010-09-27
I used a package called wireshark to take the trace. It's a network sniffing program that shows you the contents of the packets on the wire. It's in the repositories. But it can be hard understanding the results. You are looking for an HTTP GET request, and the line I showed you is from the http header.

---

### Post by finny388 on 2010-09-29
Well this all boils down to Firefox not being consistent across platforms. It's not a deal breaker or anything but if I'm curious again in the future I'll post at Mozilla.

Since I am clear on how Ubuntu sorts now I'll mark this solved.

Thanks cogs!
Finny

---

