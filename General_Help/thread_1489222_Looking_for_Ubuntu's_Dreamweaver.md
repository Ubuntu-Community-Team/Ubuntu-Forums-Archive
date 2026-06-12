---
title: "Looking for Ubuntu's Dreamweaver"
date: 2010-05-20
forum: General Help
---

### Post by TerraAnt on 2010-05-20
I recently installed Ubuntu on my laptop, so I'm rather new at this. I'm looking for an open-source software that would allow me to build websites with. When I did that on Windows, I used Dreamweaver and I really like how it works. Is there an open-source software that is comparable?

---

### Post by zaphod777 on 2010-05-20
I never used dream weaver but I am using KompoZer. It works pretty well but it is probably not as feature rich as Dreamweaver. 

I created my wifes web page using it. [www.ilovemestylist.com]("http://www.ilovemestylist.com")

---

### Post by ztrange on 2010-05-20
I have successfully installed and used DWCS3 and DWCS4 portable editions (no install needed package you can search for in google  like this 'dreamweaver cs3 portable rapidshare') with wine. Check the wine app db to get ome instructions as i cant recall what i did when i installed it.

---

### Post by SeanBlader on 2010-05-21
You need two things

[http://www.w3.org/standards/webdesign/htmlcss](http://www.w3.org/standards/webdesign/htmlcss)

And then open up a command line and type "gedit" and press enter. 

There's your dreamweaver.

---

### Post by arst06d on 2010-05-21
Amaya looks a decent candidate.

```
http://www.w3.org/Amaya/
```

---

### Post by TerraAnt on 2010-05-21
Do you guys know anything about either Quanta Plus or Bluefish Editor? I got both of them installed, but I'll need to learn the programs. Would be nice to know a thing or two about them before I commit the time.

---

### Post by ztrange on 2010-05-22
If you are interested in the graphic wysiwyg editor dreamweaver offers; I can't help you. However, if you only use code view and would like something with similar capabilities, I would highly recommend geany, it even has some IDE features like variable autocompletion that make it a great editor.

---

### Post by sdalgl72 on 2010-05-22
These blog posts might help: [http://ubuntulinuxhelp.com/series/building-a-web-developer-designer-pc/](http://ubuntulinuxhelp.com/series/building-a-web-developer-designer-pc/)

Great little blog to I've been engrossed the past couple of days

---

### Post by TerraAnt on 2010-06-01
Thanks lots for the info. I'll try two or three programs, see which ones I might like.
I normally used only the code view in Dreamweaver, and used an external browser to preview. But I'm very new to the html tags, so I'd like to use something that would show me a list of possible tags as I type, at least until I get better at this.

---

### Post by cryptotheslow on 2010-06-01
I used to love Dreamweaver back in my Windows days but I always used to  find myself in code view to finish stuff off and add lots of odds and  sods quirks to make pages behave correctly in different browsers.

After coming over to Ubuntu I missed an app that gave the apparent ease  of putting together a page quickly - and I use apparent deliberately. I  started using Bluefish and within a month or so of very casual use (I'm  not a web designer by profession) I found I had finally bothered to gain  an understanding of the various HTML doctypes and reasons for using  them, and my grasp and use of complex CSS had advanced hugely.

Now I can rustle up a fully strict standards compliant HTML/PHP + CSS  based site from a blank document in Bluefish in about half the time it  used to take me with Dreamweaver. And as a bonus, there's next to no  browser specific shenanigans - in fact I use just one CSS trick for IE  to do with centreing content on a page.

The resulting code is also far more readable and much smaller - making  ongoing maintenance and updates so much simpler.

It was at times a frustrating learning curve for sure, but well worth  the time invested.

Places I found invaluable along the way:

[http://www.w3schools.com/](http://www.w3schools.com/) for  HTML and CSS tutorials and ongoing refreshers when memory failed

[http://validator.w3.org/](http://validator.w3.org/) & [http://jigsaw.w3.org/css-validator/](http://jigsaw.w3.org/css-validator/)  get in the habit of validating your code and fixing any issues before  pulling your hair out trying to debug it

[http://www.alistapart.com/articles/doctype/](http://www.alistapart.com/articles/doctype/)  a brief rational look at html doctypes without a lot of the hyperbole  and anal musing that appears on many other discussions of the subject

[http://csscreator.com/forum/css-layouts](http://csscreator.com/forum/css-layouts)  a really helpful CSS forum site for those late nights when you ~really~  can't figure out what you are doing wrong with your layout. Be advised -  best to make sure your code at least validates before posting it up  there for scrutiny :)


As for being on-topic... I have no idea about any Dreamweaver  equivalents for Ubuntu, sorry! :D

*Edit to add:* FireBug plugin for Firefox.... you won't regret it ;)

---

### Post by James78 on 2010-06-01
The best programs by far, and closest to dreamweaver to me, are Kate, KWrite, or KDevelop 4 (get it by enabling the backports repo). KDevelop 4 is the one that is nearly fully featured, syntax highlighting and everything, it's great. I suggest you check it out. :)

---

### Post by fragos on 2010-06-01
I only code in HTML and CSS with Gedit but also open the file I'm editing with Epiphany to see how it renders. When ever I save in Gedit the Epiphany rendering is updated. Finally I use Gftp to download the new pages.

---

### Post by TerraAnt on 2010-06-03
I'll try some of the suggestions. By the way, I really liked Firebug. Is there a way to save the changes that I make using Firebug? I haven't seen a *save* button.

---

### Post by computerx138 on 2010-06-03
I use editors for PHP, HTML, CSS and Javascript. I've gone through dozens in my time. One of the most important features for me is intelligent tooltips.

Aptana: Used to have wonderful PHP/HTML support, but they since palmed it all off to Eclipse PDT team.

Eclipse PDT or derivative: Works fine, but I find the Java IDE works a little too slowly for me in Linux.

Komodo Edit (free version of ActiveState's Komodo IDE): Amazing tool tip support for everything I've thrown at it. This is currently the only editor I've actually considered paying for. Doesn't nag you to upgrade, and has Windows and Mac versions too.

---

### Post by 3rdalbum on 2010-06-03
For a while, Kompozer didn't work, so I used Seamonkey Composer (which is the project that Nvu and then Kompozer came from).

Recently I've discovered Gwrite - it's even more basic than Seamonkey and it has a couple of bugs, but it's fine for just editing an existing website. Make sure you grab the latest version from their website, the one in the Ubuntu repositories is already out of date.

---

### Post by cryptotheslow on 2010-06-03
> **TerraAnt said:**
> I'll try some of the suggestions. By the way, I really liked Firebug. Is there a way to save the changes that I make using Firebug? I haven't seen a *save* button.

There is no save option as you are actually editing the page pulled down from the webserver. It's just a neat way of quickly drilling down to the element you need and being able to manipulate it easily to see what works best. Any changes you will have to aad to your own local copy and re-upload the file.

---

### Post by TerraAnt on 2010-06-04
Too bad about the no-save-button in Firebug. It's got everything I need. I know about the issue of editing a page from the Internet, but if I'm editing my own HTML file that's on my computer, a save option would be nice. Maybe in the future.

---

### Post by zaphod777 on 2010-06-04
> **fragos said:**
> I only code in HTML and CSS with Gedit but also open the file I'm editing with Epiphany to see how it renders. When ever I save in Gedit the Epiphany rendering is updated. Finally I use Gftp to download the new pages.

I'm not sure if it is the font color or backgrounds but your page looks pretty retro from back in the day. 

Tables have always been a little tough for me to do from a text editor. I like to get my general layout then go in and manually adjust things in the code as needed for optimizations, CSS, and javascript where needed. 

Plus my wife likes to be able to type her text in herself since my Japanese isn't quite there yet. She isn't that patient to scan through the code.

---

### Post by fragos on 2010-06-04
> **zaphod777 said:**
> I'm not sure if it is the font color or backgrounds but your page looks pretty retro from back in the day. 

Tables have always been a little tough for me to do from a text editor. I like to get my general layout then go in and manually adjust things in the code as needed for optimizations, CSS, and javascript where needed. 

Plus my wife likes to be able to type her text in herself since my Japanese isn't quite there yet. She isn't that patient to scan through the code.
Thanks for the interesting comment, gives me something to think about. Perhaps my age is showing, I'm 67. The look may also be impacted by working with a subset of HTML and CSS so my sites will work in almost any browser. I'm very concerned about performance which also puts some bounds on me. Now that IE6 is getting closer to death I've started using bits of HTML5 and transparent PNGs and plan to experiment while learning new things.

---

### Post by zaphod777 on 2010-06-04
I'm no web design expert either I guess I should try working a bit harder on it though it seams like half the jobs out there these days are for web administrators not server admins.

You can do some pretty sweet things these days now though.

---

### Post by sxmaxchine on 2010-06-04
doesnt have a visual designer but it is a realy good program for creating webpages. [bluefish]("http://bluefish.openoffice.nl/")

however a program with a visual designer is kompozer however it not as good as dreamweaver but it is free and open-source.

---

### Post by cfmarshall on 2010-09-25
I crossed over to Ubuntu a couple of years back. Was using PHPEd for heavy coding and Dreamweaver for play. I've used most of the PHP IDE's mentioned but my favourite is Netbeans ([http://netbeans.org/](http://netbeans.org/)). As for a Dreamweaver lookey-likey the closest I've see is Quanta Plus ([http://quanta.kdewebdev.org/](http://quanta.kdewebdev.org/)). It has a split screen WYSIWYG editor which isn't as polished as Dreamweaver but goes far enough.

---

