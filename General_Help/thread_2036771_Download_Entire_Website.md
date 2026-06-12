---
title: "Download Entire Website?"
date: 2012-08-02
forum: General Help
---

### Post by HoCo xXSamXx on 2012-08-02
Is there any application that would allow me to download an entire website to an HTML or PDF file? I belong to a Mincraft community that has just died :'(, and I want to have the forums saved to my compuer. Any ideas?

Hoco

---

### Post by Dylan1473 on 2012-08-02
I've used Httrack for this purpose before. You can install it from the software center or with sudo apt-get install httrack in the terminal.

---

### Post by HoCo xXSamXx on 2012-08-02
I have tried this, but when I try to use it, Google Chrome gives me an error saying that it cannot find the directory:

[IMG]http://i1168.photobucket.com/albums/r481/HoCo_xXSamXx/Googleerror.png[/IMG]

---

### Post by Dylan1473 on 2012-08-02
Weird. What's in that directory? Are you sure the website got copied correctly?

---

### Post by HoCo xXSamXx on 2012-08-02
It doesn't exist. There is no "website" directory in Home. Should I make one?

---

### Post by Dylan1473 on 2012-08-02
I'd think it would've been made automatically when you copied the website. This might seem obvious but did you already try copying it again? I guess it might be worth a shot otherwise, but if the directory doesn't exist the files for the website probably don't either. When you copied the website did you save it somewhere special? I don't think it'd be in the websites folder then, that could by why.

EDIT: By which I mean, what did you put for the base path when you started the project?

EDIT AGAIN: Wait, I know what's wrong! You probably opened the web site BROWSER, not the web site COPIER. Httrack makes two applications, one for browsing the websites and one for copying them. The browsing one doesn't work since you haven't copied yet, have you? You need to use the copying one

---

### Post by HoCo xXSamXx on 2012-08-02
Well when I open the application this is what I see:

[IMG]http://i1168.photobucket.com/albums/r481/HoCo_xXSamXx/first.png[/IMG]

But when I select a language or press next I see this:

[IMG]http://i1168.photobucket.com/albums/r481/HoCo_xXSamXx/next.png[/IMG]

---

### Post by Dylan1473 on 2012-08-02
That's very strange, it brings up another page for me. Um...have you tried reinstalling? If anyone else is watching this, do they know if httrack needs a web server? I have one on my machine for unrelated reasons, could that be why? I wouldn't think so.

EDIT: Okay, can you tell me what your /usr/share/httrack/html/server directory looks like? Is there a file called step2.html in there?

---

### Post by HoCo xXSamXx on 2012-08-02
Re installed from software center. Same problem. (First time i installed from the command line).

I have also heard of the wget command? Anyone know that that is?

---

### Post by Dylan1473 on 2012-08-02
The wget command is a sort of direct download thing. So you can grab something from a web link and download it into your current directory. It might work for single pages (I've never tried) but I don't think it'd work for whole web sites.

What about that directory? What's in there? Maybe you're missing the html file for the page somehow.

EDIT: Oh how about that, you *can* use wget for an entire website. _[Here's a tutorial]("http://www.linuxjournal.com/content/downloading-entire-web-site-wget")_.

---

### Post by HoCo xXSamXx on 2012-08-02
OK, I preformed this
```
wget -r http://www.linkycraft.net/
```

Where is it saved to? How can I view it?

---

### Post by Dylan1473 on 2012-08-02
It's probably saved in your home directory unless you changed it before running that command with the cd command. That wasn't the full command you should've run and you might only have the home page. You can probably open it by double clicking. You might have to right click it and select chromium to run it with, but probably not.

---

### Post by HoCo xXSamXx on 2012-08-02
Well the command is still executing. Ill get back to you when its done.

---

### Post by Dylan1473 on 2012-08-02
Wait, it's still going? Maybe it works by itself after all. In case that doesn't work, it probably should look like this:
```

wget \      
--recursive \      
--no-clobber \      
--page-requisites \      
--html-extension \      
--convert-links \      
--restrict-file-names=windows \      
--domains linkycraft.net \ 
--no-parent \          
http://www.linkycraft.net/home

```I have to step out for a bit but I'll probably be back in approximately 45 minutes if you still need help.

EDIT: In case you have bandwidth caps to deal with (and chances are you do) you'll want to keep an eye on that. You don't want to end up trying to download the entire internet or something and losing access/getting charged a bunch at the end of the month. You can press Ctrl-C at any time to cancel it if you feel it's necessary.

---

### Post by ing.tani on 2012-08-03
Try this:
wget -r -p -e robots=off -U mozilla <URL address>

---

### Post by Habitual on 2012-08-03
```
wget -p --convert-links www.domain.com

```

---

