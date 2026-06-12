---
title: "Can you tile an image in metacity"
date: 2010-07-06
forum: General Help
---

### Post by samriggs on 2010-07-06
I am trying to get the titlebar to tile in metacity instead of stretch, I was wondering if this is possible or not.
I am using the crux theme but it stretches the pixmap instead.
I heard that others tried and could not do it, but can do it in gtk with pixmap.
I seen the tutorial for metacity and it had this tag
```
<tile name="other_drawing_operations" tile_width="10" tile_height="10"/>
```
but how to use it with an image if that is possible I don't know how to do it.
I am new at this obviously and I am hopping someone has a solution or answer if this is possible or not.
This tag above does not describe in the tutorial if it can be used for an image in a titlebar or not.
Thanks for any help in advance, its much appreciated.
Sam

---

### Post by samriggs on 2010-07-07
Ok no one seems to know the answer to this one, I did find one answer from a person named Issiah who made the tiling work on a theme
Here is the code
```
<draw_ops name="titlebar_middle"><image filename="titlebar-mid-focused.png" height="height" width="width" x="0" y="0" />
  </draw_ops><draw_ops name="title">
  <image filename="titlebar-left-focused.png" height="height" width="object_width" x="0" y="0" />
  <tile height="height" name="titlebar_middle" tile_height="24" tile_width="25" width="width" x="6" />
  <image filename="titlebar-right-focused.png" height="height" width="object_width" x="width - object_width" y="0" />
</draw_ops>
```
I tired this in the crux theme way to many ways to try and get it to work but it still didn't work for me.

This is the chunk of code I want to add a tile into
```
<piece position="titlebar">
    <draw_ops>

      <image filename="active-left-top-border.png" 
             colorize="gtk:bg[SELECTED]"
             x="0" y="0" width="object_width" height="height"/>

      <image filename="active-right-top-border.png" 
             x="width - object_width" y="0" width="object_width" height="height"/>

      <image filename="active-top-center-left.png" 
             colorize="gtk:bg[SELECTED]"
             x="4" y="0" 
             width="(left_width + ButtonWidth + IconTitleSpacing + title_width) `min`
                    (width - right_width - 3 * ButtonWidth - CenterTitlePieceWidth * height / 22 - 3)" 
             height="height"/>

      <image filename="active-top-center-mid-left.png" 
             colorize="gtk:bg[SELECTED]"
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width) `min` (width - object_width * height / 22 - right_width - 3 * ButtonWidth)) + 1"
             y="0" width="object_width * height / 22" height="height"/>

      <image filename="active-top-center-mid-right.png" 
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width) `min` (width - object_width * height / 22 - right_width - 3 * ButtonWidth)) + 1"
             y="0" width="object_width * height / 22" height="height"/>

      <image filename="active-top-center-right.png"
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width + CenterTitlePieceWidth * height / 22) `min` (width - 3 * ButtonWidth - right_width)) + 1"
             y="0"
             width="(width - title_width - left_width - ButtonWidth - IconTitleSpacing - CenterTitlePieceWidth * height / 22 - right_width) `max` (3 * ButtonWidth)"
             height="height"/>

    </draw_ops>
  </piece>

```

the image I want to tile is ```
active-top-center-left.png
```

Every time I try it, I get errors and it refuses to work for me.

One thing I did try was this

```
<piece position="titlebar">
[COLOR=Red]<draw_ops name="titlebar"><image filename="active-top-center-left.png" height="height" width="width" x="0" y="0" />
  </draw_ops>[/COLOR]
    <draw_ops>

      <image filename="active-left-top-border.png" 
             colorize="gtk:bg[SELECTED]"
             x="0" y="0" width="object_width" height="height"/>

      <image filename="active-right-top-border.png" 
             x="width - object_width" y="0" width="object_width" height="height"/>

     [COLOR=Red]<tile height="height" name="titlebar_middle" tile_height="22" tile_width="48" width="width" x="6" />[/COLOR]

      <image filename="active-top-center-mid-left.png" 
             colorize="gtk:bg[SELECTED]"
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width) `min` (width - object_width * height / 22 - right_width - 3 * ButtonWidth)) + 1"
             y="0" width="object_width * height / 22" height="height"/>

      <image filename="active-top-center-mid-right.png" 
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width) `min` (width - object_width * height / 22 - right_width - 3 * ButtonWidth)) + 1"
             y="0" width="object_width * height / 22" height="height"/>

      <image filename="active-top-center-right.png"
             x="((left_width + ButtonWidth + IconTitleSpacing + title_width + CenterTitlePieceWidth * height / 22) `min` (width - 3 * ButtonWidth - right_width)) + 1"
             y="0"
             width="(width - title_width - left_width - ButtonWidth - IconTitleSpacing - CenterTitlePieceWidth * height / 22 - right_width) `max` (3 * ButtonWidth)"
             height="height"/>

    </draw_ops>
  </piece>

```

But no way that worked, I am new to this so I am sure , well the errors tell me, it's way out of wack.
If anyone can help out on this one please do, I will really appreciate it as I am sure a lot of others will also as there is not much out there about tiling in metacity, besides the tutorial at gnome which does not explain how to solve this kind of issue.
Thanks again for any help anyone can provide in this.

---

