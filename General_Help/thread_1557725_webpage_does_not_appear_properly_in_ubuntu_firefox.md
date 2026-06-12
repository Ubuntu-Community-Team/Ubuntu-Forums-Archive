---
title: "webpage does not appear properly in ubuntu firefox but no error in windows all browse"
date: 2010-08-21
forum: General Help
---

### Post by mayankgupta2005 on 2010-08-21
Hello, i am newbie, and i am developing my website.
My web-site's pages appears to be fine when i open in any browser (including IE, Firefox, Chrome) in windows..
but when i  open the same website page  in Ubuntu-Firefox the page has lots of css and font errors..is this a problem in ubuntu or my website?
my website link: [http://www.beakkon.com](http://www.beakkon.com) 
any suggestion on how to fix it? 
i am also attaching the  snippet of a page of my website when it is opened in Ubuntu-firefox.


Thanks in advance!! :)

---

### Post by apoorvumang on 2010-08-21
It works fine on chrome in ubuntu. Dunno why firefox messes it up.

---

### Post by mayankgupta2005 on 2010-08-21
yes!! it works fine in chrome on ubutnu, its only firefox, have not come across something like this ever before!

---

### Post by mendhak on 2010-08-21
I think it's this:

```

.content {
    position:absolute;
    left:15px;
    width: 670px;
    color:#3e3d3c;
    overflow:hidden;
    font:Arial, Helvetica, sans-serif;
    font-size:14px;
    text-align:justify;
}

```

The DIV is absolutely positioned and you're hiding anything that goes beyond its constraints.  This may be related to a lot of the other absolute positioning going on in the CSS - have you considered using relative layouts and floating the elements within containers?  The layout of your page is pretty simple - it resembles a blog page, so I don't think you should be going down the absolute route.

---

### Post by mayankgupta2005 on 2010-08-21
umm sorry, but i did not get you...u mean to say i should change the div positioning from absolute to relative? and the layout is simple for now and does resemble a blog page, i will be changing the right bar layout soon and i think i need to go through the absolute mode in that. can you suggest something else, if i have got you correct.
Thanks. :)

---

