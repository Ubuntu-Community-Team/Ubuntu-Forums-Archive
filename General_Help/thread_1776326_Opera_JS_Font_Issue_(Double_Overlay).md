---
title: "Opera JS Font Issue (Double Overlay)"
date: 2011-06-06
forum: General Help
---

### Post by gresavage on 2011-06-06
Hey i've been having a problem recently viewing fonts on some web pages. The fonts are visible, however opera is doing this weird thing where it looks like the font is placed on the page twice with a minor offset. I have found no forum topics posted about this in any of the usual forum sites (my.opera, ubuntuforums, etc.)

I'm using opera 11. And I suspect that the issue lies with java since it doesn't happen on a lot of web pages (about 50%). I will attach a few screen caps so that you can see what i'm talking about.

I'm running Ubuntu 11.04 (2.6.38-9) and have had this problem since Ubuntu 10.10 and opera 10.

Any help is much appreciated!

here are examples of my issue:

[IMG]http://img607.imageshack.us/img607/8215/screenshotfl.png[/IMG]
[IMG]http://img695.imageshack.us/img695/8093/screenshot1rap.png[/IMG]

hopefully someone can at least tell me where this problem originates so I can try to fix it myself, unfortunately i'm not savvy enough when it comes to these kinds of things!

i have also posted this thread in my.opera forums however i trust the support from here (esp for linux issues) moreso than there!

---

### Post by gresavage on 2011-08-16
i just checked the style sheets and stylings using opera dragonfly. I don't believe it has to do with the css... since i was not able to debug it by process of elimination (enabling/disabling properties such as text-shadow, font-weight etc.) However the issue does seem to be isolated solely to specific level headears such as h3, and h2 (perhaps more but i didn't check). h4 does not seem to have this issue.

also checked errors in opera dragonfly and only found issues pertaining to the box-shadow property, this is not likely the culprit. 

I am at a complete loss here! any help from someone more savvy than me would be greatly appreciated.

---

### Post by gresavage on 2011-08-16
i think i found the source of the error. It originates from the font-family property when the value is inherit... i'm not sure where to tell where it's inheriting from... i think the font family with the issues is arial. i will make a style sheet to force sans-serif instead of arial, maybe actually pick a font family later

---

### Post by gresavage on 2011-08-16
okay so he is how i fixed this (in case anyone comes across this problem again)

[LIST=1] i created a css file using any text editor like gedit, kate, bluefish
[*]i named that file arialfix.css and put it in my styles folder ( /home/tom/.opera/styles/user/)
[*]in that file i put the following code:
```

@charset "utf-8";
* {
font-family: sans-serif !important;
}

```
[*]then i told opera to use my style sheet by going to menu-->page-->style-->manage modes
[*]i then directed it to my new file by going to the =display= taB and typed in the path to the css file (in my case /home/tom/.opera/styles/user/arialfix.css)
[*]then in the =presentation modes= tab under the =author mode= column i checked the box that says "Use my style sheet" and clicked =OK=
[*]restart opera and everything looks fine
[/LIST]

the issue with this fix is that it forces all the selectors to assign a value of =sans-serif= to the property =font-family=. which will cause all the fonts on all the webpages to be =sans-serif=. If you wish to change this all you have to do is some quick css to specify a selector that you wish not to be sans-serif and assign it as such. I suggest you use the !important tag so you make sure to put your css hack into the top level of the cascade priority.

I didn't change any of the selectors to anything other than sans-serif because i don't care that much. hope this may help anyone else in the future... and hopefully someone can still come along and tell me why it's doing that![LIST=1]
[/LIST]

---

