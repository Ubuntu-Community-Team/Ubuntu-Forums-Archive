---
title: "Any way to adjust window shadows?"
date: 2011-04-29
forum: General Help
---

### Post by leeman101 on 2011-04-29
I find the window shadows a little phony against a light background.  Not a big deal, but just curious if there is a way to change this.  Tried through Compiz, but that didn't actually change anything.

---

### Post by leeman101 on 2011-04-29
Anyone? :/

---

### Post by leeman101 on 2011-04-29
No one ever responds to me. lol oh well...

---

### Post by mc4man on 2011-04-29
Well - I only know for ambiance, mainly because I thought MS's decision to use a 45px shadow was too much. (and i have a feeling person working on this also thought so

Any here i open this in a text editor (gksudo gedit -
/usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml

At this section (currently line 426, highlighted in blue) I change the radius="45.0" to something lower, using 24.0 here

```
<!-- FRAME STYLE -->
<frame_style name="normal_focused" geometry="frame_geometry_normal">
	<piece position="title" draw_ops="draw_title_text_normal"/>
   	<piece position="titlebar" draw_ops="draw_title"/>
   	<piece position="left_edge" draw_ops="draw_frame"/>
   	<piece position="right_edge" draw_ops="draw_frame"/>
   	<piece position="bottom_edge" draw_ops="bottom_edge"/>
	<button function="left_left_background" state="normal" draw_ops="left_left_background_focused_normal"/>
	<button function="left_middle_background" state="normal" draw_ops="left_middle_background_focused_normal"/>
	<button function="left_right_background" state="normal" draw_ops="left_right_background_focused_normal"/>
	<button function="left_left_background" state="prelight" draw_ops="left_left_background_focused_normal"/>
	<button function="left_middle_background" state="prelight" draw_ops="left_middle_background_focused_normal"/>
	<button function="left_right_background" state="prelight" draw_ops="left_right_background_focused_normal"/>
	<button function="left_left_background" state="pressed" draw_ops="left_left_background_focused_pressed"/>
	<button function="left_middle_background" state="pressed" draw_ops="left_middle_background_focused_pressed"/>
	<button function="left_right_background" state="pressed" draw_ops="left_right_background_focused_pressed"/>
	<button function="right_left_background" state="normal" draw_ops="right_left_background_focused_normal"/>
	<button function="right_middle_background" state="normal" draw_ops="right_middle_background_focused_normal"/>
	<button function="right_right_background" state="normal" draw_ops="right_right_background_focused_normal"/>
	<button function="right_left_background" state="prelight" draw_ops="right_left_background_focused_normal"/>
	<button function="right_middle_background" state="prelight" draw_ops="right_middle_background_focused_normal"/>
	<button function="right_right_background" state="prelight" draw_ops="right_right_background_focused_normal"/>
	<button function="right_left_background" state="pressed" draw_ops="right_left_background_focused_pressed"/>
	<button function="right_middle_background" state="pressed" draw_ops="right_middle_background_focused_pressed"/>
	<button function="right_right_background" state="pressed" draw_ops="right_right_background_focused_pressed"/>
	<button function="menu" state="normal" draw_ops="menu_focused_normal"/>
	<button function="menu" state="prelight" draw_ops="menu_focused_prelight"/>
	<button function="menu" state="pressed" draw_ops="menu_focused_normal"/> 
	<button function="minimize" state="normal" draw_ops="minimize_focused_normal"/>
	<button function="minimize" state="prelight" draw_ops="minimize_focused_prelight"/>
	<button function="minimize" state="pressed" draw_ops="minimize_focused_pressed"/>
	<button function="maximize" state="normal" draw_ops="maximize_focused_normal"/>
	<button function="maximize" state="prelight" draw_ops="maximize_focused_prelight"/>
	<button function="maximize" state="pressed" draw_ops="maximize_focused_pressed"/>
	<button function="close" state="normal" draw_ops="close_focused_normal"/>
	<button function="close" state="prelight" draw_ops="close_focused_prelight"/>
	<button function="close" state="pressed" draw_ops="close_focused_pressed"/>
	[COLOR="Blue"]<shadow radius="24.0" opacity="0.75" color="#abde4f" x_offset="1" y_offset="4"/>[/COLOR]
	<padding left="5" right="5" bottom="5"/>
</frame_style>
```

I also go with 0px borders, right at the very top of the file (2nd section), changing the three 1's to 0

```
<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
 	<distance name="left_width" value="[COLOR="Blue"]0[/COLOR]"/>
	<distance name="right_width" value="[COLOR="Blue"]0[/COLOR]"/>
	<distance name="bottom_height" value="[COLOR="Blue"]0[/COLOR]"/>
	<distance name="left_titlebar_edge" value="10"/>
ect, ect.

```

Maybe this could be done elsewhere, but I find simple to do here

Edit - if doing when the text editor is open go edit > preferences > 'display line numbers', makes life easy, a log out/in is required after editing

---

### Post by leeman101 on 2011-04-30
Thank you!   Works.  :-]

---

