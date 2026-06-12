---
title: "Crux Theme Issue"
date: 2010-07-04
forum: General Help
---

### Post by samriggs on 2010-07-04
Hello everyone
First timer here, my wife and I just switched over to ubuntu full time finally and I am now working on a theme for both our laptops, I am using the crux theme but I hit a snag and since I have never coded a theme before I am trying to plow through it.
On line 416 of metacity-theme.xml file it has this code
```
 <image filename="active-top-center-left.png" 
             colorize="gtk:bg[SELECTED]"
             x="4" y="0" 
             width="(left_width + ButtonWidth + IconTitleSpacing + title_width) `min`
                    (width - right_width - 3 * ButtonWidth - CenterTitlePieceWidth * height / 22 - 3)" 
             height="height"/>
```It makes the background stretch in this one area, which is great but I want it to repeat instead so I can add a design in that area to tile instead of stretching it.
If anyone knows an answer to fix this or if you have worked with the crux theme and found a fix for no stretching but repeating instead I would greatly appreciate an answer to this one.
Maybe I am looking in the wrong part of the code to fix this as I know the rubens theme has a fix but it is in the gtk file instead where it says stretch = FALSE
I looked up the tutorial seen this
```
<tile name="other_drawing_operations" tile_width="10"  tile_height="10"/>
```I want to tile the image and I am new this does anyone know how to tile an image instead of having it stretched?
This is my first week at learning this so I am a newbie at it.
Thanks again for any help in advance.
Sam

---

