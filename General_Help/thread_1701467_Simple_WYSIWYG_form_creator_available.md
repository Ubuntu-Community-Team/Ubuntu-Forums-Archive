---
title: "Simple WYSIWYG form creator available?"
date: 2011-03-06
forum: General Help
---

### Post by A Traveller on 2011-03-06
Hi All.

I was wondering if there was a simple free WYSIWYG program available for Ubuntu that could be used to create a simple form which meets the following criteria.

1) I would like it to be viewable in a web browser in which the form can then be filled out.

2) The form is just to be used as an example of which order various fields will be arranged on the page and which fields will use check boxes or radio buttons or drop down lists, etc. The form isn't actually going to be uploaded anywhere or require anyone to 'submit' it, however, I must be able to view the form in the web browser window, populate it, enter data and make selections, etc.

3) I wish the form to have various headings, such as Section 1, Section 2, etc. Can this be done within the software or does this have to be done separately (by creating a basic HTML page with the headings/text, etc) and then the source code of the form pasted in at the relevant points?

4) Does suitable software exist which meets the above criteria and also allow various fields to display information depending on what is chosen in other fields? For example, if there are five drop down fields labeled Continent, Country, County/State, City and Town, would it be possible to choose, for example, Europe from the Continent drop down, which would then only show the countries from Europe in the Country drop down list, then if UK is selected, only Counties in the UK would be listed in the County/State drop down list, etc?

I know if it's a WYSIWYG program, then it really doesn't matter what kind of computer/programing 'language' the form is created in, but just out of curiosity, can the above be achieved with just simple HTML or do things like Visual Basic, PHP, JavaScript, etc need to be used in order to create such a form?

The following website seems ok, but can it do what I have requested in point 4 above? Also, I would prefer to use a software program located on my pc and not an online program, however, this isn't totally essential.

[http://www.jotform.com/](http://www.jotform.com/)

If anyone can kindly provide any suggestions, it would be really appreciated. Thanks.

---

### Post by cchhrriiss121212 on 2011-03-06
Kompozer should handle that, should be in the software centre.

---

### Post by wiggly81 on 2011-03-06
> I know if it's a WYSIWYG program, then it really doesn't matter what kind of computer/programing 'language' the form is created in, but just out of curiosity, can the above be achieved with just simple HTML or do things like Visual Basic, PHP, JavaScript, etc need to be used in order to create such a form?
the form can be created in HTML anything used to process the form would usually be PHP Javascript ASP etc...

---

### Post by vat with tux on 2011-03-06
I'm not sure whether it will work or not. But if u r not satisfied with Komposer or any other editor u may try installing Dreamviewer inside wine.:)

---

### Post by A Traveller on 2011-03-07
Thank you for all the replies and suggestions.

I have now installed Kompozer and there doesn't seem to be any help available regarding creating forms. I have also looked at Charles Cooke’s User Guide and couldn't find anything helpful there regarding forms. I may have to join their forums as creating forms in Kompozer does not seem to be quite so straightforward to use.

I have no idea how to have one drop down list show a list depending on what is chosen in another drop down list. cchhrriiss121212, are you sure this can be done in Kompozer?

Thanks.

---

### Post by wiggly81 on 2011-03-07
NO that requires AJAX

---

### Post by A Traveller on 2011-03-08
Hi wiggly81, thanks for the reply. So I'm back to square one and back to my original question in my post. Is there any other program I could use that does what I require?

I came across the script at the link below and pasted it into Kompozer, but it will require some fiddling if I am to figure out how to add a label to the left of the boxes, etc.

[http://www.javascriptkit.com/script/script2/multiplecombo.shtml](http://www.javascriptkit.com/script/script2/multiplecombo.shtml)

Another thing with Kompozer is that when I create fields, they appear perfectly aligned in preview mode and while creating them, however, when saved as an HTML file and opened in a browser, they are not aligned correctly.

Thanks.

---

### Post by bodhi.zazen on 2011-03-08
Honestly I advise you use bluefish.

You then view the resulting document with firefox.

The end result is cleaner code that is easier to maintain then a WYSIWYG editor.

As you have found, WYS is not always WYG using such tools and the code is often sloppy, harder to maintain, and has difficulty passing validation.

---

### Post by A Traveller on 2011-03-08
Thanks for the reply bodhi.zazen.

Do I need to know anything about code, scripts, etc, in order to use Bluefish for what I want? I don't know any code, script, etc at all!!

Thanks.

---

### Post by Flyers2391 on 2011-03-08
> **bodhi.zazen said:**
> Honestly I advise you use bluefish.

You then view the resulting document with firefox.

The end result is cleaner code that is easier to maintain then a WYSIWYG editor.

As you have found, WYS is not always WYG using such tools and the code is often sloppy, harder to maintain, and has difficulty passing validation.

Thanks, I had issues with Kompozer before but continued to use it and then modify the rest in code (which I am admittedly very weak on as it's been a while so I've done any semi-real programming).  I'm going to check this out and see how I like it

---

### Post by bodhi.zazen on 2011-03-08
> **A Traveller said:**
> Thanks for the reply bodhi.zazen.

Do I need to know anything about code, scripts, etc, in order to use Bluefish for what I want? I don't know any code, script, etc at all!!

Thanks.

> **Flyers2391 said:**
> Thanks, I had issues with Kompozer before but continued to use it and then modify the rest in code (which I am admittedly very weak on as it's been a while so I've done any semi-real programming).  I'm going to check this out and see how I like it

It takes a little time, but I highly advise you learn the code.

You can start with komposer , but look at the code ;)

bluefish is also nice as it automates much of the coding.

After learning the code I wrote my web site with vim (hard core I know), but my point is, if you are going to do web pages, IMO, it is a much more efficient use of time to learn the html / php / javascript / etc . It takes less time then attempting to debug code written by WYSIWYG editors.

There are a number of online tutorials and nothing beats firing up opera / firefox / and chromium and viewing the actual result. You will find the various browsers all have nuances.

Personally I gave up trying to code of IE, IE is less and less popular but if you wish fire up IE with wine.

---

### Post by A Traveller on 2011-03-08
Thanks for the helpful reply, bodhi.zazen.

As mentioned in my original post, the form is only to be used as an example of a form and is not going to be part of a website or be uploaded or published anywhere. I don't need anything fancy, as long as it allows radio buttons, check boxes, text boxes, labels, headings/sections and multiple combo drop down list boxes, then that would be sufficient.

I take it from the replies here and from research that at least javascript will be needed for the multiple combo boxes, but there seems to be a few scripts posted on various websites which I could paste into the script generated by a WYSIWYG program and then replace the contents of the drop down lists with my own and try to figure out how to add labels etc next to the drop down lists.

At the moment, I have no time to go through a time-consuming learning process as my aim is not to learn at this stage but find a simple way to produce a form.

I may give jotform another try and see what results are produced by pasting in javascript for multiple combo drop down boxes/lists.

Thanks.

---

### Post by bodhi.zazen on 2011-03-08
> **A Traveller said:**
> Thanks for the helpful reply, bodhi.zazen.

As mentioned in my original post, the form is only to be used as an example of a form and is not going to be part of a website or be uploaded or published anywhere. I don't need anything fancy, as long as it allows radio buttons, check boxes, text boxes, labels, headings/sections and multiple combo drop down list boxes, then that would be sufficient.

I take it from the replies here and from research that at least javascript will be needed for the multiple combo boxes, but there seems to be a few scripts posted on various websites which I could paste into the script generated by a WYSIWYG program and then replace the contents of the drop down lists with my own and try to figure out how to add labels etc next to the drop down lists.

At the moment, I have no time to go through a time-consuming learning process as my aim is not to learn at this stage but find a simple way to produce a form.

I may give jotform another try and see what results are produced by pasting in javascript for multiple combo drop down boxes/lists.

Thanks.

I understand, but ...

In my experience it takes time to do these things, and "hacking" something together takes as much time (or longer sometimes) then it does to learn the code.

Good luck to you. If you run into a problem, take a look at any of the various on line tutorials and try to use the code you download as a template.

---

### Post by A Traveller on 2011-03-08
Thanks bodhi.zazen, will keep that in mind and possibly give it a try when I have the time.

Don't know if it makes any difference, wiggly81, but I have just noticed that jotform uses AJAX.

Thanks for all the help and advice everyone. It is really appreciated.

---

