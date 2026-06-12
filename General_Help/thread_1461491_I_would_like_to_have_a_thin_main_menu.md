---
title: "I would like to have a thin main menu"
date: 2010-04-24
forum: General Help
---

### Post by alindgr1 on 2010-04-24
I was not sure where to put this, so I threw it in here.

I am trying to make my main menu as thin as it is when I apply a theme called "3am" that I downloaded from Gnone-look.  I have plowing through the gtkrc all morning and part of last night, but I cannot figure how to do what I want.  I have attached two screenshots.  One with the thin main menu and one with the main menu at the default thickness.

In the mean time, I am going to keep looking around the google results to see what I can figure it out.

Thanks to all ahead of time.

---

### Post by VCoolio on 2010-04-24
Find the style that controls the menuitems, then add / configure an ythickness line, so it will look like this:

```

style "blah"
{
  ...(FG/BG entries)
  ythickness                = <int>
  ...
  ...(optionally the following:)
  engine "blah"
  {
     ...
  }
}

```

---

