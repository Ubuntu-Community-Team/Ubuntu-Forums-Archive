---
title: "Can anyone help with updating gtkrc to include latest Murrine options?"
date: 2010-06-11
forum: General Help
---

### Post by wersdaluv on 2010-06-11
Based on their Facebook fan page, Murrine has been evolving a lot lately. I don't know where to find the latest options, though. The [Dichotomy theme]("https://wiki.ubuntu.com/Artwork/Incoming/Lucid/Dichotomy") features new Murrine options, but it may not be the most updated one. 

Here's Dichotomy's **engine "murrine"** section.
```
	engine "murrine" 
	{
		animation		= FALSE # FALSE = disabled, TRUE = enabled
		arrowstyle		= 0     # 0 = normal arrows, 1 = filled arrows
		#border_colors		= { "#ffffff", "#ffffff" } # colors used on borders of many widgets
		border_shades		= { 1.1, 1.0 } # gradient to draw on border
		#gradient_colors	= { "#ffffff", "#ffffff", "#ffffff", "#ffffff" } # colors used on gradient of many widgets
		comboboxstyle		= 1     # 0 = normal combobox, 1 = colorized combobox below arrow
		colorize_scrollbar	= TRUE  # FALSE = disabled, TRUE = enabled
		contrast		= 0.8   # 0.8 for less contrast, more than 1.0 for more contrast on borders
		focus_color 		= mix (0.7, @bg_color, shade (3.5, @tooltip_bg_color))
		glazestyle		= 0     # 0 = flat, 1 = curved, 2 = concave, 3 = top-curved, 4 = beryl
		glow_shade		= 1.05  # sets glow amount for buttons or widgets
		glowstyle		= 4     # 0 = top, 1 = bottom, 2 = top and bottom, 3 = center (vertical), 4 = center (horizontal) 
		gradient_shades		= {1.03,1.01,1.01,0.95} # default: {1.1,1.0,1.0,1.1}
		highlight_shade		= 1.02  # set highlight amount for buttons or widgets
		lightborder_shade	= 1.2   # sets lightborder amount for buttons or widgets
		lightborderstyle	= 0     # 0 = lightborder on top side, 1 = lightborder on all sides
		listviewheaderstyle	= 1     # 0 = flat, 1 = glassy, 2 = raised
		listviewstyle		= 2     # 0 = nothing, 1 = dotted, 2 = solid line
		menubaritemstyle	= 1     # 0 = menuitem look, 1 = button look
		menubarstyle		= 0     # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
		menuitemstyle		= 1     # 0 = flat, 1 = glassy, 2 = striped
		menustyle		= 0     # 0 = no vertical menu stripe, 1 = display vertical menu stripe
		prelight_shade		= 0.95  # shade level for scrollbar's slider, comboboxstyle(1), and prelight state with gradient_colors
		progressbarstyle	= 0     # 0 = no stripes, 1 = diagonal stripes, 2 = vertical stripes 
		reliefstyle		= 3     # 0 = flat, 1 = inset, 2 = shadow, 3 = shadow with gradient, 4 = stronger shadow with gradient
		rgba			= FALSE  # FALSE = disabled, TRUE = enabled
		roundness		= 2     # 0 = squared, 1 = old default, more will increase roundness
		separatorstyle		= 1     # 0 = standard, 1 = smooth
		scrollbarstyle		= 2     # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles
		shadow_shades		= { 0.9, 0.7 } # draw gradient on shadow of some widgets
		sliderstyle		= 1     # 0 = nothing added, 1 = handles
		spinbuttonstyle		= 0     # 0 = no seperator, 1 = with separator
		stepperstyle		= 1     # 0 = standard, 1 = integrated stepper handles, 2 = squared steppers with round slider
		textstyle		= 0     # 0 = normal text, 1 = inset, 2 = inverted inset
		toolbarstyle		= 0     # 0 = flat, 1 = glassy, 2 = gradient
		trough_shades		= { 1.14, 0.96 } # draw gradient on trough of GtkScrollbar and GtkProgressbar
	}
}
```

What else can you add?

---

