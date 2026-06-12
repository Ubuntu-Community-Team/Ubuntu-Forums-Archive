---
title: "Why there's a different went viewing my site using IE and firefox mozilla?"
date: 2009-06-25
forum: General Help
---

### Post by cas1 on 2009-06-25
The following attach image are taken from firefox and running ubuntu OS as you can see the [SIZE=4]red cross[/SIZE] which i've highlighted, there's this chinese and korean wording which is suppose to be at the lower portion below HOME section but now it appear on top and also i'm not able to access Services, Company, News, Blogs as well as Testimonial while using my cursor there, whereas while i'm using Internet explorer i don't have the above issue, it look normal while i'm accessing the above site running IE with window
 
Btw i've downloaded all the requirement like flash, swf when i access my site when it prompt me to download but then why i'm still encountering the above, anyone care to help, would appreciate very much :(
 
[IMG]http://img.photobucket.com/albums/v174/olivero/mozilla5.jpg[/IMG]

---

### Post by lovinglinux on 2009-06-26
I think the problem is bad web design. There is a lot of web designers who build their sites for IE, which is the worst browser in terms of following web standards. So when you view the page on a standard compliant web browser like Firefox things get messy. It's not a Firefox problem.

I believe the issue here is a div layer which incorrectly placed in the screen and with a z-index that puts it above other elements of the page. So when you try to click the Products menu you actually click the div layer and nothing happens.

Another possible scenario happens when you use an extension like AdBlock plus, which blocks some elements on the page, causing some div layers to be misplaced, if their positioning are relative to blocked elements.

To solve this problem you could install the [Remove it Permanently](https://addons.mozilla.org/en-US/firefox/addon/521) extension to remove the problematic layer from the page when it is rendered on your browser.

---

### Post by earthpigg on 2009-06-26
i suggest trying to view the web page in Opera and Chrome before assuming its a FF issue -- if it looks different in every browser ***_except_*** IE, then we know to blame IE.

---

### Post by jolo on 2009-06-27
This ias a great and important question, which is about ALL systems to view the Internet.

I do web design and I have HAD it with IE. 

It is simple, 

**Firefox adheres to the International standards of the W3C Worldwide Web Consortium Standards and Microsoft, Microsft, intentionally doesn't. **

I know tell me clients that all coding I do, will be compatible with Industry Standards and to use Firefox and if someone is using IE, I simple will not support it, although I have links in front of web pages to install it. I have had enough of having to have separate sections of code to allow for the archaic, proprietary nonsense of IE. I am not the only one like this, as IE is finally getting a lot of pressure from Programmers to allow for the Internationally accepted standards.  

IE 6 is no0t compatible with IE 7 which is not compatible with IE 8. Microsoft is about industry control, rather than technical excellence.

However, it is very possible that two different systems using the same version of Firefox might have their screens look differently, due differences in graphics cards and the use of older, more limited cards that might limit the fonts and colors that can be displayed. 

The lack of commitment to standards, also is one of the reasons that IE has more security holes, than there are potholes in New York City. 




> **earthpigg said:**
> i suggest trying to view the web page in Opera and Chrome before assuming its a FF issue -- if it looks different in every browser ***_except_*** IE, then we know to blame IE.

---

### Post by lovinglinux on 2009-06-27
> **lovinglinux said:**
> I think the problem is bad web design. There is a lot of web designers who build their sites for IE, which is the worst browser in terms of following web standards. So when you view the page on a standard compliant web browser like Firefox things get messy. It's not a Firefox problem.

I just realized that the site is yours, so I want to apologize if I offended you with my comments about bad design. It wasn't my intention.

I think would be better to move this thread in the [Art & Design](http://ubuntuforums.org/forumdisplay.php?f=16) or the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forums.

---

### Post by dcstar on 2009-06-27
There are literally hundreds of reason why web pages render differently in different browsers.

I have found that unmatched string tags will be ignored by some browsers but totally confuse others, unmatched/incorrect tags in tables can also do the same thing.

It is not all about propriety browsers doing things "their way" - although IE is certainly guilty of far too many of these things - so just because something does render ok in any browser does not guarantee that the underlying HTML code is actually correct.

---

### Post by cas1 on 2009-06-28
I did try running opera, firefox and both oso have the same lines, except in IE. I'm really loss as what has it got to do with? No matter what thanks to all for the contribution, once i change the design layout for the template from horizontal to vertical, the lines went off but when viewing from IE, firefox and opera there's still slight difference as in the layout :(

---

### Post by DeMus on 2009-06-28
> **cas1 said:**
> I did try running opera, firefox and both oso have the same lines, except in IE. I'm really loss as what has it got to do with? No matter what thanks to all for the contribution, once i change the design layout for the template from horizontal to vertical, the lines went off but when viewing from IE, firefox and opera there's still slight difference as in the layout :(

It is exactely as Lovinglinux said: the cause is bad webdesign. Designers just follow MS since they think that is the standard (as put down by the W3 consortium).
In fact MS wants to build their own standard since they think it is better, Firefox, Opera and all others follow W3 which is the real standard.
What you could do is enlarge your page (make more overhead) by adding different parts for IE and the rest. Adding overhead is the MS way (look at a page which is made with Frontpage, 95% is overhead) so I wonder if you want this. It will take much longer to download the page.

---

### Post by cas1 on 2009-06-28
> **DeMus said:**
> It is exactely as Lovinglinux said: the cause is bad webdesign. Designers just follow MS since they think that is the standard (as put down by the W3 consortium).
In fact MS wants to build their own standard since they think it is better, Firefox, Opera and all others follow W3 which is the real standard.
What you could do is enlarge your page (make more overhead) by adding different parts for IE and the rest. Adding overhead is the MS way (look at a page which is made with Frontpage, 95% is overhead) so I wonder if you want this. It will take much longer to download the page.
 
I dunno how true ur word is or here's ubuntu forum, no offence though, but then i've went to a well known forum site recently and discover there's lot's of similar lines on it's home page when running unbuntu with mozilla but then when using xp and running IE dun have this issue
 
Hmm so is due to ubuntu or window, i've yet to tell.......

---

### Post by DeMus on 2009-06-28
> **cas1 said:**
> I dunno how true ur word is or here's ubuntu forum, no offence though, but then i've went to a well known forum site recently and discover there's lot's of similar lines on it's home page when running unbuntu with mozilla but then when using xp and running IE dun have this issue
 
Hmm so is due to ubuntu or window, i've yet to tell.......

Which well known forum site is this? Look [_here_]("http://www.w3.org/") please and read all about The Standard in webdesign.
It is as with everything: MS wants to rule. They do not accept it when somebody outside MS makes the standard. It should be their standard. Well, it's not.
Something they also can not accept is the fact that in web addresses the forward slash "/" is used, as does Unix and Linux in their path/to/folder, and not the Backward slash "\" as used by MS (C:\).
Just accept the fact that MS wants to use their own standards, their own inventions but in the case of webdesign, the standard has been set by somebody else and it is NOT the MS way.

---

### Post by cyclobs on 2009-06-28
yeah IE is just a horrible program to code for.

personally i don't even bother with it. if a webpage is screwed up on IE i make i just direct someone to a real web broweser. 

tho most of my work isn't really designed for professional use. like orginisation sites or anything like that

---

### Post by SeanBlader on 2009-06-28
> **cas1 said:**
> I dunno how true ur word is or here's ubuntu forum, no offence though, but then i've went to a well known forum site recently and discover there's lot's of similar lines on it's home page when running unbuntu with mozilla but then when using xp and running IE dun have this issue
 
Hmm so is due to ubuntu or window, i've yet to tell.......

Before you blame Ubuntu, why don't you try Firefox on Windows? That way you're isolating the issue between one variable and then you'll know if it's Ubuntu or Windows since in both cases you will have tested with Firefox. 

What you're doing is like finding your car has a really rough ride, so you try another car on a different road and it drives smooth, but then you get back in your car on the same road it was on previously and find that it's bumpy again. It could turn out that your car is an off road vehicle, and the second car you're testing is a rail car. Hard to make a comparison when you aren't isolating the variables.

My personal opinion is that you're a troll and shouldn't be writing web pages anyway. If you REALLY wanted to know what the problem was, then you'd have given us the address of the site, and we'd have told you already. So to me it's obvious that you came here to bash Ubuntu, but instead, I think we should post you to failblog.org.

---

### Post by cyclobs on 2009-06-28
all this talk about web development is making me want to code something

---

### Post by The Cog on 2009-06-28
If there is a difference in appearance between IE and Firefox, my first assumption would be that I have found yet another point where IE doesn't adhere to the standards. However, this isn't always the case. Firefox does have renderng bugs too. I would suggest that you try looking at the site in IE, Firefox, Opera and Safari. These will cover the majority of your viewers, and give you confidence that if those 4 agree then any other browseer is likely to agree too.

If you do this with all your web pages, you will very likely find that it is IE which is always the odd one out and the others generally follow the standards.

---

