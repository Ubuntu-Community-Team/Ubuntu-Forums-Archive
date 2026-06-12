---
title: "Firefox close buttons and tab size"
date: 2010-08-01
forum: General Help
---

### Post by ekengle on 2010-08-01
I'm looking for help with the size of the min,max, close buttons in the corner of firefox.  They are very small and I can't find a way to increase them.  I've tried different themes but that doesn't work.

The other thing I would like to increase is the size of the tabs.  I DON'T WANT TO MAKE THEM LONGER, I WANT TO MAKE THEM TALLER so they are easier to hit when laptop is hooked to TV.  Right now they are very short and I use the mouse on the arm of my chair (cloth) and  it's a little difficult to hit them.  

I've searched and read tips for the past week and none have what I need.  They all tell me how to make the tabs longer or shorter and how to add or remove close boxes in the individual tabs.  These don't do what I need done.  Can these simple things be done in firefox or am I SOL?

---

### Post by dcstar on 2010-08-02
> **ekengle said:**
> I'm looking for help with the size of the min,max, close buttons in the corner of firefox.  They are very small and I can't find a way to increase them.  I've tried different themes but that doesn't work.

The other thing I would like to increase is the size of the tabs.  I DON'T WANT TO MAKE THEM LONGER, I WANT TO MAKE THEM TALLER so they are easier to hit when laptop is hooked to TV.  Right now they are very short and I use the mouse on the arm of my chair (cloth) and  it's a little difficult to hit them.  

I've searched and read tips for the past week and none have what I need.  They all tell me how to make the tabs longer or shorter and how to add or remove close boxes in the individual tabs.  These don't do what I need done.  Can these simple things be done in firefox or am I SOL?

The control icons have nothing to do with any application including Firefox, they are controlled by the Window Manager and the themes that are used.

Have a look at this:

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/160311)

---

### Post by lovinglinux on 2010-08-02
Install [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/versions/"), then create a new style for it through the status bar menu and add the following code:

```

@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

/*Tabs Toolbar*/
#TabsToolbar{
 min-height: 35px !important;
 max-height: 40px !important;
}
```

Tweak the values according to your taste.

---

