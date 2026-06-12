---
title: "What's the html / css for how &quot;code&quot; is shown in ubuntuforums?"
date: 2009-08-16
forum: General Help
---

### Post by quixote on 2009-08-16
I've tried "view source" and even dug up the ubuntuforums' stylesheet, but I can't figure this out.  How do I get an element to have scrollbars when it's too wide for its parent box?  I.e. like the "code" element on these forums```
which has a box with a scrollbar without messing up the formatting if it goes on and on and on and on and on.
```

I figure it has to be some combination of css properties "display: something-or-other" and/or "overflow: something-or-other" but nothing I do works.  Instead I get scrollbars on the whole browser window.

I realize this isn't an ubuntu question, but a css question.  I apologize for that, but the ubuntuforums are by far the best around, so I'm hoping it's not too bad to ask here. :)

---

### Post by TheBuzzSaw on 2009-08-16
```
div
{
    width: 400px;
    overflow: auto;
}
```

Try that.

---

### Post by techstop on 2009-08-16
Here's the code of what you just posted;

> <pre class="alt2" dir="ltr" style="border: 1px inset ; margin: 0px; padding: 6px; overflow: auto; width: 640px; height: 34px; text-align: left;">which has a box with a scrollbar without messing up the formatting if it goes on and on and on and on and on.</pre>

It looks like the effect is a combination of specifying a width and height for the "code" element, plus the css "overflow" property for dealing with what happens when the content exceeds the dimensions of the element;

[http://www.w3schools.com/Css/pr_pos_overflow.asp](http://www.w3schools.com/Css/pr_pos_overflow.asp)

---

### Post by quixote on 2009-08-16
Thanks for the replies.  The problem with BuzzSaw's suggestion is that the scrollbars show up on the browser window, not the element (images, in my case), and the images still push the boundaries of their parent div so they blow up the formatting.  The same is true of overflow:scroll and even overflow:hidden.

I did look at the source on the pre tag, but when I try to use that styling, all it does is set the width to 640px.  It doesn't put the image into a scrollable box of its own.  I found the relevant stylesheet by looking at the <head>, and checked out class=alt2, but that's just a couple of things about font size or something (don't remember right now but it wasn't relevant.)

What I did discover since I posted was that you can wrap the element inside another div such as this:```
.handheldbox {
	display:block;
	width:300px;
	height:300px;
	overflow:scroll;
	}
```  That works, but the problem is I'd have to go back through about 200 posts, find the ones with images, and edit those to put that new div around them!  Aack.

Is there a way in css, or somehow, to say that you want a given element to be inside another div?  I've tried```
.thecontent img:before {'<div class="handheldbox">'}
and
.thecontent img:after {'</div>'} 
```but all that does is draw a box with nice scrollbars and then plop the outsize image on top of it, not inside it.  Very frustrating.

(This is all for the purpose of making a handheld stylesheet for my web site.  Everything is scaling nicely after about three solid days of fighting with it, except these blankety-blank images!)

---

### Post by TheBuzzSaw on 2009-08-17
Did you modify my code to fit your situation? You're not supposed to just target all div tags. All you need is the overflow: auto specified with a width and height on a single element. Target .myDiv or something.

In order to wrap your images, you'll probably have to use Javascript (to do it en masse).

---

### Post by credobyte on 2009-08-17
Assuming that the *code box* contents are not being formated, why not to use textarea ( which will auto-add scrollbars on overflow ) ?
```
<TEXTAREA NAME="ubercode" COLS="29" ROWS="7"></TEXTAREA>
```

---

### Post by quixote on 2009-08-17
Thanks for the replies.  Buzzsaw, yes, I've been trying different overflow settings just on img tags that appear in  ".thecontent" div.  The problem is that "overflow: auto" puts the scroll bars on the whole browser window, whereas I want them just on the image itself.

Credobyte: I like the idea of trying textarea in future.  I'll try that out.

Re the javascript: yes, I was coming to that conclusion myself.  I think it'll be faster, for me, to just do them one by one because I can't even produce "hello, world" in javascript without major debugging.

---

