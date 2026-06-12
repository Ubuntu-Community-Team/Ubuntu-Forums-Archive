---
title: "Simple GTKRC editing problem"
date: 2009-08-09
forum: General Help
---

### Post by dumblebee100 on 2009-08-09
lately Im editing my gtkrc for my preferences so I came up with some problems and one hell of a flat theme ...basically I was inspired by HMMXP theme in windows I just want to make a replica of that but in linux style ( I mean using all extra things which are provided by linux gtkrc) ( dont feel me as windows fan ..bcz Im not )

well here comes ..I have a editing problem with the gtkrc ...
all I wanted is the feature in screenshot 11 but Im stuck with style in screenshot 10 

I mean to say that I want gradient colour in tabs of any application ...since I get a line type of color in every app then if I change then I would obviously get in every app

then next ones is I want a window border of some color say white 
even after editing many values in xml file Im stuck with border just to the title bar and not total window ...you can see that effect in screenshot 12

well after editing the rectangle color="FFF000" I get the yellow colour but not to the whole window 
I get to only the title bar ..
and there is a black outline to the rest of the window which I want to make it white ...so I need some help from here

I included my gtkrc and metacity-theme-1.xml for ur reference ..ofcourse they are just edited and not my own

gtkrc
```

# Please keep this gtkrc in sync with the other ones from Clearlooks based themes.

gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#648BCB\nselected_fg_color:#ffffff\ntext_color:#000000\nbg_color:#ededed\ntooltip_bg_color:#FFFFBF"
#gtk-color-scheme = "tooltip_bg_color:#FFFFBF\nselected_bg_color:#648BCB\nbase_color:#ffffff"
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=22,22:gtk-button=16,16"

style "default" {
	xthickness = 1
	ythickness = 1

	#######################
	# Style Properties
	#######################

	GtkWidget::focus-line-width = 1

	GtkButton::child-displacement-x = 1
	GtkButton::child-displacement-y = 1
	GtkButton::default-border = { 0, 0, 0, 0 }
	GtkCheckButton::indicator-size = 14

	GtkPaned::handle-size = 6
	GtkRange::trough-border = 0
	GtkRange::slider-width = 14
	GtkRange::stepper-size = 14

	GtkScale::slider-length = 30
	GtkScale::trough-side-details = 1

	GtkScrollbar::min-slider-length = 30
	GtkMenuBar::internal-padding = 0
	GtkExpander::expander-size = 16
	GtkTreeView::expander-size = 14
	GtkTreeView::vertical-separator = 0
	GtkToolbar     ::internal-padding     = 1

	GtkMenu::horizontal-padding = 0
	GtkMenu::vertical-padding = 0

	WnckTasklist::fade-overlay-rect = 0
	# The following line hints to gecko (and possibly other appliations)
	# that the entry should be drawn transparently on the canvas.
	# Without this, gecko will fill in the background of the entry.
	GtkEntry::honors-transparent-bg-hint = 1

	####################
	# Color Definitions
	####################
	bg[NORMAL]        = "#EDEDED"
	bg[PRELIGHT]      = "#f2f2ee"
	bg[SELECTED]      = "#708CA4"
	bg[INSENSITIVE]   = "#e2e2de"
	bg[ACTIVE]        = "#FFFFFF"

	fg[NORMAL]        = "#000000"
	fg[PRELIGHT]      = "#000000"
	fg[SELECTED]      = "#ffffff"
	fg[INSENSITIVE]   = "#969696"
	fg[ACTIVE]        = "#000000"

	text[NORMAL]      = "#000000"
	text[PRELIGHT]    = "#000000"
	text[SELECTED]    = "#ffffff"
	text[INSENSITIVE] = "#000000"
	text[ACTIVE]      = "#000000"

	base[NORMAL]      = "#ffffff"
	base[PRELIGHT]    = "#eaeaea"
	base[SELECTED]    = "#648BCB"
	base[INSENSITIVE] = "#ffffff"
	base[ACTIVE]      = "#B9B8AA"


	engine "clearlooks" {
		colorize_scrollbar = FALSE
		reliefstyle = 1
		menubarstyle = 0
		toolbarstyle = 0
		animation = TRUE
		radius = 0.1
		style = INVERTED

		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}
}

style "wide" {
	xthickness = 2
	ythickness = 2
	bg[SELECTED] = @selected_bg_color
}

style "wider" {
	xthickness = 3
	ythickness = 3
	bg[SELECTED] = @selected_bg_color
}

style "spinbutton" {

	engine "clearlooks" {
		hint = "spinbutton"
	}
}

style "scale" = "button" {
	xthickness = 2
	ythickness = 2

	engine "clearlooks" {
		hint = "scale"
	}
}

style "vscale" {

	engine "clearlooks" {
		hint = "vscale"
	}
}

style "hscale" {

	engine "clearlooks" {
		hint = "hscale"
	}
}

style "scrollbar" {
	xthickness = 2
	ythickness = 2

	engine "clearlooks" {
		hint = "scrollbar"
	}
}

style "hscrollbar" {

	engine "clearlooks" {
		hint = "hscrollbar"
	}
}

style "vscrollbar" {

	engine "clearlooks" {
		hint = "vscrollbar"
	}
}

style "notebook_bg" {
bg[NORMAL]        = shade (1.04, @bg_color)
}

style "button" {
	xthickness = 1
	ythickness = 0
	bg[NORMAL]   = shade (1.98, @bg_color)
#	bg[PRELIGHT] = shade (1.04, @bg_color)
	bg[ACTIVE]   = shade (0.92, @bg_color)
bg[PRELIGHT]      = mix(0.60, shade (1.05,@bg_color), @selected_bg_color)
}

style "notebook" {
	xthickness = 1
	ythickness = 0
}

style "statusbar" {

	engine "clearlooks" {
		hint = "statusbar"
	}
}

style "comboboxentry" {

	engine "clearlooks" {
		# Note:
		# If you set the appears-as-list option on comboboxes in the theme,
		# then you should set this hint on the combobox instead.
		hint = "comboboxentry"
	}
}

style "menubar" {

	engine "clearlooks" {
		hint = "menubar"
	}
}

style "menu" {
	xthickness = 0
	ythickness = 0

	bg[NORMAL]        = shade (1.08, @bg_color)
}

style "menu_item" {
	xthickness = 2
	ythickness = 2
	bg[PRELIGHT] = mix(0.90, shade (1.05, @selected_bg_color), @tooltip_bg_color)
	bg[SELECTED] = mix(0.90, shade (1.05, @selected_bg_color), @tooltip_bg_color)
	fg[PRELIGHT] = @selected_fg_color
}

style "frame_title" {

	fg[NORMAL]        = lighter (@fg_color)
}

style "treeview" {
	xthickness = 2
	ythickness = 2

	engine "clearlooks" {
		hint = "treeview"
	}
}

style "progressbar" {
	xthickness = 1
	ythickness = 1

	bg[SELECTED] = @selected_bg_color
	fg[PRELIGHT] = @base_color

	engine "clearlooks" {
		radius = 0.1

		hint = "progressbar"
	}
}

# This style is based on the default style, so that the colors from the button
# style are overriden again.
style "treeview_header" = "default" {
	xthickness = 2
	ythickness = 1

	engine "clearlooks" {
		hint = "treeview-header"
	}
}

style "tooltips" {
	xthickness = 4
	ythickness = 4

	bg[NORMAL]        = @tooltip_bg_color
	fg[NORMAL]        = @tooltip_fg_color
}

style "nautilus_location" {

	bg[NORMAL]        = mix (0.60, shade (1.05, @bg_color), @selected_bg_color)
}

# Wrokaroudn style for places where the text color is used instead of the fg color.
style "text_is_fg_color_workaround" {

	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for menus where the text color is used instead of the fg color.
style "menuitem_text_is_fg_color_workaround" {

	text[NORMAL]      = @fg_color
	text[PRELIGHT]    = @selected_fg_color
	text[SELECTED]    = @selected_fg_color
	text[ACTIVE]      = @fg_color
	text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for places where the fg color is used instead of the text color.
style "fg_is_text_color_workaround" {

	fg[NORMAL]        = @text_color
	fg[PRELIGHT]      = @text_color
	fg[SELECTED]      = @selected_fg_color
	fg[ACTIVE]        = @selected_fg_color
	fg[INSENSITIVE]   = darker (@bg_color)
}

# Style to set the toolbar to use a flat style. This is because the "New" button in
# Evolution is not drawn transparent. So if there is a gradient in the background it will
# look really wrong.
# See http://bugzilla.gnome.org/show_bug.cgi?id=446953.
style "evo_new_button_workaround" {

	engine "clearlooks" {
		toolbarstyle = 0
	}
}


###############################################################################
# The following part of the gtkrc applies the different styles to the widgets.
###############################################################################

# The default style is applied to every widget
class "GtkWidget" style "default"

class "GtkSeparator" style "wide"
class "GtkFrame" style "wide"
class "GtkCalendar" style "wide"
class "GtkEntry" style "wider"

class "GtkSpinButton" style "spinbutton"
class "GtkScale" style "scale"
class "GtkVScale" style "vscale"
class "GtkHScale" style "hscale"
class "GtkScrollbar" style "scrollbar"
class "GtkHScrollbar" style "hscrollbar"
class "GtkVScrollbar" style "vscrollbar"

# General matching follows. The order is choosen so that the right styles override
# each other. EG. progressbar needs to be more important than the menu match.
widget_class "*<GtkNotebook>" style "notebook_bg"
# This is not perfect, it could be done better.
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkLayout>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkViewport>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkScrolledWindow>" style "notebook_bg"

widget_class "*<GtkButton>" style "button"
widget_class "*<GtkNotebook>" style "notebook"
widget_class "*<GtkStatusbar>*" style "statusbar"

widget_class "*<GtkComboBoxEntry>*" style "comboboxentry"
widget_class "*<GtkCombo>*" style "comboboxentry"

widget_class "*<GtkMenuBar>*" style "menubar"
widget_class "*<GtkMenu>*" style "menu"
widget_class "*<GtkMenuItem>*" style "menu_item"

widget_class "*.<GtkFrame>.<GtkLabel>" style "frame_title"
widget_class "*.<GtkTreeView>*" style "treeview"

widget_class "*<GtkProgress>" style "progressbar"

# Treeview headers (and similar stock GTK+ widgets)
widget_class "*.<GtkTreeView>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCTree>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkList>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCList>.<GtkButton>" style "treeview_header"

# The window of the tooltip is called "gtk-tooltip"
##################################################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
##################################################################
widget "gtk-tooltip*" style "tooltips"

##########################################################################
# Following are special cases and workarounds for issues in applications.
##########################################################################

# Workaround for the evolution ETable (bug #527532)
widget_class "*.ETable.ECanvas" style "treeview_header"
# Workaround for the evolution ETree
widget_class "*.ETree.ECanvas" style "treeview_header"

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "nautilus_location"

# Work around for http://bugzilla.gnome.org/show_bug.cgi?id=382646
# Note that this work around assumes that the combobox is _not_ in appears-as-list mode.
widget_class "*.<GtkComboBox>.<GtkCellView>" style "text_is_fg_color_workaround"
# This is the part of the workaround that fixes the menus
widget "*.gtk-combobox-popup-menu.*" style "menuitem_text_is_fg_color_workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the base color.
widget_class "*<GtkListItem>*" style "fg_is_text_color_workaround"
# GtkCList also uses the fg color to draw text on top of the base colors.
widget_class "*<GtkCList>" style "fg_is_text_color_workaround"
# Nautilus when renaming files, and maybe other places.
widget_class "*<EelEditableLabel>" style "fg_is_text_color_workaround"

# See the documentation of the style.
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "evo_new_button_workaround"
``` 

my metacity-theme-1.xml
```
<?xml version="1.0"?>

<metacity_theme>
<info>
  <name>SimplySmooth</name>
  <author>Link Dupont &lt;link@subpop.net&gt;</author>
  <copyright>Â 2004 Link Dupont</copyright>
  <date>April, 2004</date>
  <description>Based on Industrial by Tuomas Kuosmanen &lt;tigert@ximian.com&gt; and SmoothBox by Andrew Johnson &lt;ajgenius@ajgenius.us&gt;</description>
</info>
 
<frame_geometry name="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="1"/>
  <distance name="right_width" value="1"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="4"/>
  <distance name="right_titlebar_edge" value="4"/>
  <aspect_ratio name="button" value="1"/>
  <distance name="title_vertical_pad" value="4"/>
  <border name="title_border" left="2" right="2" top="1" bottom="1"/>
  <border name="button_border" left="2" right="2" top="4" bottom="4"/>
</frame_geometry>

	<!-- strip borders off the normal geometry -->
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
	<distance name="left_width" value="0"/>
	<distance name="right_width" value="0"/>
	<distance name="bottom_height" value="0"/>
	<distance name="left_titlebar_edge" value="1"/>
	<distance name="right_titlebar_edge" value="1"/>
</frame_geometry>

<frame_geometry name="normal_small_borders" parent="normal">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
</frame_geometry>

<frame_geometry name="border" has_title="false">
  <distance name="left_width" value="1"/>
  <distance name="right_width" value="1"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <distance name="button_width" value="0"/>
  <distance name="button_height" value="0"/>
  <distance name="title_vertical_pad" value="4"/>
  <border name="title_border" left="0" right="0" top="0" bottom="0"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>

<!-- button inside padding -->
<constant name="ButtonIPad" value="3"/>
<constant name="ThickLineWidth" value="3"/>

<draw_ops name="focus_outline">
  <rectangle color="#000000"
             x="left_width-1" y="top_height-1"
             width="width-left_width-right_width+1"
             height="height-top_height-bottom_height+1"/>
  <line color="shade/gtk:bg[SELECTED]/0.45" x1="left_width-1" y1="top_height-1" 
     x2="left_width-1" y2="top_height-1"/>
  <line color="shade/gtk:bg[SELECTED]/0.45" x1="width-right_width" y1="top_height-1" 
     x2="width-right_width" y2="top_height-1"/>
  <line color="shade/gtk:bg[SELECTED]/0.65" x1="left_width-1" y1="height-bottom_height" 
     x2="left_width-1" y2="height-bottom_height"/>
  <line color="shade/gtk:bg[SELECTED]/0.65" x1="width-right_width" y1="height-bottom_height" 
     x2="width-right_width" y2="height-bottom_height"/>

</draw_ops>

<draw_ops name="corners_outline">
        <!-- ** BLACK outlines around the round corners ** -->
	<!-- top left -->
	<line color="#000000" x1="1" y1="3" x2="1" y2="4"/>
 	<line color="#000000" x1="2" y1="2" x2="2" y2="2"/>
	<line color="#000000" x1="3" y1="1" x2="4" y2="1"/>

	<!-- bottom left -->
	<line color="#000000" x1="1" y1="height-4" x2="1" y2="height-5"/>
 	<line color="#000000" x1="2" y1="height-3" x2="2" y2="height-3"/>
	<line color="#000000" x1="2" y1="height-2" x2="4" y2="height-2"/>

	<!-- top right -->
	<line color="#000000" x1="width-2" y1="3" x2="width-2" y2="4"/>
	<line color="#000000" x1="width-3" y1="2" x2="width-3" y2="2"/>
	<line color="#000000" x1="width-4" y1="1" x2="width-5" y2="1"/>

	<!-- bottom right -->
	<line color="#000000" x1="width-2" y1="height-4" x2="width-2" y2="height-5"/>
	<line color="#000000" x1="width-3" y1="height-3" x2="width-3" y2="height-3"/>
	<line color="#000000" x1="width-4" y1="height-2" x2="width-5" y2="height-2"/>

</draw_ops>

<draw_ops name="corners_hilight_unfocused">

  <!-- ** corner hilight for left top ** -->
  <line color="shade/gtk:bg[NORMAL]/1.3" x1="2" y1="3" x2="2" y2="4"/>
  <line color="shade/gtk:bg[NORMAL]/1.3" x1="3" y1="2" x2="4" y2="2"/>

  <!-- ** corner hilight for left bottom ** -->
  <line color="shade/gtk:bg[NORMAL]/1.4" x1="2" y1="height-4" x2="2" y2="height-5"/>
  <line color="shade/gtk:bg[NORMAL]/0.9" x1="3" y1="height-3" x2="4" y2="height-3"/>

  <!-- ** corner hilight for right top ** -->
  <line color="shade/gtk:bg[NORMAL]/0.8" x1="width-3" y1="3" x2="width-3" y2="4"/>
  <line color="shade/gtk:bg[NORMAL]/0.9" x1="width-4" y1="2" x2="width-4" y2="2"/>

  <!-- ** corner hilight for right bottom ** -->
  <line color="shade/gtk:bg[NORMAL]/0.7" x1="width-3" y1="height-4" x2="width-3" y2="height-5"/>
  <line color="shade/gtk:bg[NORMAL]/0.7" x1="width-4" y1="height-3" x2="width-5" y2="height-3"/>

</draw_ops>

<draw_ops name="corners_hilight">

  <!-- ** corner hilight for left top ** -->
  <line color="shade/gtk:bg[SELECTED]/1.55" x1="2" y1="3" x2="2" y2="4"/>
  <line color="shade/gtk:bg[SELECTED]/1.55" x1="3" y1="2" x2="4" y2="2"/>

  <!-- ** corner hilight for left bottom ** -->
  <line color="shade/gtk:bg[SELECTED]/1.4" x1="2" y1="height-4" x2="2" y2="height-5"/>
  <line color="shade/gtk:bg[SELECTED]/0.9" x1="3" y1="height-3" x2="4" y2="height-3"/>

  <!-- ** corner hilight for right top ** -->
  <line color="shade/gtk:bg[SELECTED]/0.8" x1="width-3" y1="3" x2="width-3" y2="4"/>
  <line color="shade/gtk:bg[SELECTED]/0.9" x1="width-4" y1="2" x2="width-4" y2="2"/>

  <!-- ** corner hilight for right bottom ** -->
  <line color="shade/gtk:bg[SELECTED]/0.7" x1="width-3" y1="height-4" x2="width-3" y2="height-5"/>
  <line color="shade/gtk:bg[SELECTED]/0.7" x1="width-4" y1="height-3" x2="width-5" y2="height-3"/>

</draw_ops>

<!-- ** interlace ** -->
<draw_ops name="title_tile">
<!--  <tint color="black" x="0" y="0" width="width" height="0" alpha="0.1"/>
  <tint color="white" x="0" y="1" width="width" height="1" alpha="0.05"/>-->
</draw_ops>

<draw_ops name="bevel_maximized_unfocused">

  <!-- ** 3d beveled frame ** -->
<!--  <rectangle color="#000000" filled="false"
             x="0" y="0"
             width="width-2"
             height="height-2"/>

  <rectangle color="shade/gtk:light[NORMAL]/1.6" filled="false"
             x="1" y="1"
             width="width-3"
             height="height-3"/>
  <line color="shade/gtk:light[SELECTED]/1.6" x1="0" y1="1" 
     x2="0" y2="title_height + 4"/>

  <rectangle color="gtk:bg[NORMAL]" filled="true"
             x="0" y="2"
             width="width"
             height="title_height + 4"/>
-->
<!-- ** fancy gradient along the title bar (total bar even with buttons background and menu background) ** -->
  <gradient type="horizontal" x="0" y="0" width="width - 4" height="title_height + 6">
	<!--<color value="shade/gtk:bg[SELECTED]/0.9"/>
	<color value="shade/gtk:bg[SELECTED]/1.1"/>-->
	<color value="#929292"/>
	<color value="#D3D3D3"/>
  </gradient>

<!-- changes the rectangle border when the window is unfocused-->
  <rectangle color="#FFFFFF" filled="false"
       x="0" y="0"
       width="width - 1"
       height="height - 1"/>


</draw_ops>

<draw_ops name="bevel_maximized">

  <!-- ** 3d beveled frame ** -->
<!--  <line color="#000000" x1="0" y1="0" 
     x2="width" y2="0"/>
  <rectangle color="shade/gtk:light[SELECTED]/1.2" filled="true"
             x="0" y="1"
             width="width"
             height="title_height + 4"/>
-->
   <!-- ** fancy gradient ** -->
  <gradient type="horizontal" x="0" y="0" width="width" height="title_height+6">
	<!--<color value="shade/gtk:bg[SELECTED]/0.9"/>
	<color value="shade/gtk:bg[SELECTED]/1.1"/>-->
	<color value="#65829C"/>
	<color value="#8AA3B8"/>

  </gradient>
<!-- fils the colour of rectangle which is below the title bar -->
<!--  <line color="#FFF000" x1="0" y1="title_height + 5" 
     x2="width" y2="title_height + 5"/>
-->
<!-- changes the rectangle border when the window is focused-->
  <rectangle color="#FFFFFF" filled="false"
       x="0" y="0"
       width="width - 1"
       height="height - 1"/>

</draw_ops>

<draw_ops name="bevel_unfocused">

  <!-- ** 3d beveled frame ** -->
<!--  <rectangle color="gtk:dark[NORMAL]" filled="false"
             x="1" y="1"
             width="width - 3"
             height="height - 3"/>
 
  <rectangle color="shade/gtk:light[NORMAL]/1.6" filled="false"
             x="1" y="1"
             width="width - 4"
             height="height - 4"/>

  <rectangle color="gtk:bg[NORMAL]" filled="true"
             x="2" y="2"
             width="width - 4"
             height="height - 4"/>
-->

<!-- ** fancy gradient along the title bar (total bar even with buttons background and menu background) ** -->
  <gradient type="horizontal" x="0" y="0" width="width" height="title_height + 6">
	<!--<color value="shade/gtk:bg[SELECTED]/0.9"/>
	<color value="shade/gtk:bg[SELECTED]/1.1"/>-->
	<color value="#929292"/>
	<color value="#D3D3D3"/>
  </gradient>

<!-- changes the rectangle border when the window is unfocused-->
  <rectangle color="#FFFFFF" filled="false"
       x="0" y="0"
       width="width - 1"
       height="height - 1"/>

</draw_ops>

<draw_ops name="round_bevel_unfocused">
  <include name="bevel_unfocused"/>
  <!--<include name="corners_outline"/>
  <include name="corners_hilight_unfocused"/>-->

</draw_ops>

<draw_ops name="bevel">

  <!-- ** 3d beveled frame ** -->
<!--  <rectangle color="blend/gtk:bg[NORMAL]/gtk:bg[SELECTED]/0.5" filled="true"
             x="2" y="title_height + 38"
             width="width-4"
             height="height-title_height-38"/>

  <rectangle color="shade/gtk:light[SELECTED]/1.2" filled="false"
             x="1" y="1"
             width="width - 2"
             height="height - 2"/>

  <rectangle color="gtk:dark[SELECTED]" filled="false"
             x="0" y="0"
             width="width - 2"
             height="height - 2"/>
-->


  <!-- ** fancy gradient ** -->
  <gradient type="horizontal" x="0" y="0" width="width" height="title_height+6">
	<!--<color value="shade/gtk:bg[SELECTED]/0.9"/>
	<color value="shade/gtk:bg[SELECTED]/1.1"/>-->
	<color value="#65829C"/>
	<color value="#8AA3B8"/>

  </gradient>
<!-- fills the colour of rectangle which is below the title bar -->
<!--  <line color="#FFF000" x1="0" y1="title_height + 5" 
     x2="width" y2="title_height + 5"/>
-->
<!--  <gradient type="horizontal" x="2" y="title_height+6" width="width - 4" height="32">
	<color value="shade/gtk:bg[SELECTED]/0.7"/>
	<color value="blend/gtk:bg[NORMAL]/gtk:bg[SELECTED]/0.5"/>
	<color value="#929292"/>
	<color value="#D3D3D3"/>

  </gradient>
-->
<!--<tile name="title_tile" tile_width="width" tile_height="2" x="1" y="1" width="width - 2" height="title_height + 5"/>
-->



<!-- changes the rectangle border when the window is focused-->
  <rectangle color="#FFF000" filled="false"
       x="0" y="0"
       width="width - 1"
       height="height - 1"/>

</draw_ops>

<draw_ops name="round_bevel">
  <include name="bevel"/>
  <!--<include name="corners_outline"/>
  <include name="corners_hilight"/>-->

  <include name="focus_outline"/>

</draw_ops>

<!-- ::: TITLES ::: -->

<draw_ops name="title_bg">
   <tile name="title_tile" tile_width="4" tile_height="10" x="0" y="2" width="(width-title_width)/2-4" height="10"/>
<!--<gradient type="horizontal" x="0" y="1" width="width" height="height">
			<color value="#000000"/>
			<color value="#000000"/>
		</gradient>-->
</draw_ops>
<draw_ops name="title_bg_unfocused">
  <tile name="title_tile" tile_width="4" tile_height="10" x="(width-title_width)/2+title_width+4" y="2" width="(width-title_width)/2-4" height="11"/>
<!--<gradient type="horizontal" x="1" y="1" width="width" height="height">
			<color value="#929292"/>
			<color value="#D3D3D3"/>
		</gradient>-->
</draw_ops>

<!-- hush! nothing to see here! move on! :^) -->
<draw_ops name="title_text">
  <title color="shade/gtk:bg[SELECTED]/0.75"
         x="(3 `max` (width-title_width)) / 2 + 1"
         y="(((height - title_height) / 2) `max` 0) + 2"/>
  <title color="shade/gtk:bg[SELECTED]/0.7"
         x="(3 `max` (width-title_width)) / 2 + 2"
         y="(((height - title_height) / 2) `max` 0) + 2"/>
  <title color="shade/gtk:bg[SELECTED]/0.4"
         x="(3 `max` (width-title_width)) / 2 + 1"
         y="(((height - title_height) / 2) `max` 0) + 1"/>
  <title color="gtk:fg[SELECTED]"
         x="(3 `max` (width-title_width)) / 2"
         y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>

<draw_ops name="title_text_unfocused">
	<title color="blend/gtk:fg[NORMAL]/gtk:bg[NORMAL]/1.1"
         x="(3 `max` (width-title_width)) / 2"
         y="((height - title_height) / 2) `max` 0"/>
</draw_ops>

<draw_ops name="title">
  <include name="title_bg"/>
  <include name="title_text"/>
</draw_ops>

<draw_ops name="title_unfocused">
  <include name="title_bg_unfocused"/>
  <include name="title_text_unfocused"/>
</draw_ops>

<!-- ::: BUTTONS ::: -->

<draw_ops name="button_bg">
  <gtk_box state="normal" shadow="out" x="0" y="0" width="width" height="height"/>
</draw_ops>

<draw_ops name="button_bg_unfocused">
  <gtk_box state="insensitive" shadow="out" x="0" y="0" width="width" height="height"/>
</draw_ops>

<draw_ops name="button_bg_prelight">
  <gtk_box state="prelight" shadow="out" x="0" y="0" width="width" height="height"/>
</draw_ops>

<draw_ops name="button_bg_pressed">
  <gtk_box state="active" shadow="in" x="0" y="0" width="width" height="height"/>
</draw_ops>

<draw_ops name="menu_button_icon"> 
  <icon  x="0"
         y="0"
         width="width" height="height"/>
</draw_ops>

<draw_ops name="menu_button_icon_unfocused"> 
  <icon  x="0"
         y="0"
         width="width" height="height" alpha="0.5"/>
</draw_ops>

<draw_ops name="menu_button_normal">
  <include name="menu_button_icon"/>
</draw_ops>
<draw_ops name="menu_button_pressed">
  <include name="menu_button_icon"/>
</draw_ops>
<draw_ops name="menu_button_unfocused">
  <include name="menu_button_icon_unfocused"/>
</draw_ops>

<draw_ops name="close_button_icon">
        <line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad+1" y1="ButtonIPad"
			x2="width - ButtonIPad" y2="height - ButtonIPad - 1"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad" y1="ButtonIPad"
			x2="width - ButtonIPad" y2="height - ButtonIPad"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad" y1="ButtonIPad+1"
			x2="width - ButtonIPad - 1" y2="height - ButtonIPad"/>

		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad" y1="height - ButtonIPad - 2"
			x2="width - ButtonIPad - 1" y2="ButtonIPad-1"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad" y1="height - ButtonIPad - 1"
			x2="width - ButtonIPad" y2="ButtonIPad-1"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			width="1"
			x1="ButtonIPad+1" y1="height - ButtonIPad - 1"
			x2="width - ButtonIPad" y2="ButtonIPad"/>
</draw_ops>

<draw_ops name="close_button_icon_unfocused">
<include name="button_bg_unfocused"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad+1" y1="ButtonIPad"
			x2="width - ButtonIPad" y2="height - ButtonIPad - 1"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad" y1="ButtonIPad"
			x2="width - ButtonIPad" y2="height - ButtonIPad"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad" y1="ButtonIPad+1"
			x2="width - ButtonIPad - 1" y2="height - ButtonIPad"/>

		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad" y1="height - ButtonIPad - 2"
			x2="width - ButtonIPad - 1" y2="ButtonIPad-1"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad" y1="height - ButtonIPad - 1"
			x2="width - ButtonIPad" y2="ButtonIPad-1"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			width="1"
			x1="ButtonIPad+1" y1="height - ButtonIPad - 1"
			x2="width - ButtonIPad" y2="ButtonIPad"/>
	</draw_ops>

	<draw_ops name="outer_bevel">
		<rectangle color="#000000"
			x="0" y="0" width="width-1" height="height-1"/>
		<line color="gtk:light[NORMAL]"
			x1="1" y1="1" x2="1" y2="height-2"/>
		<line color="gtk:light[NORMAL]"
			x1="1" y1="1" x2="width-2" y2="1"/>
		<line color="gtk:dark[NORMAL]"
			x1="width-2" y1="1" x2="width-2" y2="height-2"/>
		<line color="gtk:dark[NORMAL]"
			x1="1" y1="height-2" x2="width-2" y2="height-2"/>           
</draw_ops>

<draw_ops name="close_button_normal">
  <include name="button_bg"/>
  <include name="close_button_icon"/>
</draw_ops>
<draw_ops name="close_button_prelight">
  <include name="button_bg_prelight"/>
  <include name="close_button_icon"/>
</draw_ops>
<draw_ops name="close_button_pressed">
  <include name="button_bg_pressed"/>
  <include name="close_button_icon"/>
</draw_ops>
<draw_ops name="close_button_unfocused">
  <include name="button_bg_unfocused"/>
  <include name="close_button_icon_unfocused"/>
</draw_ops>

<draw_ops name="maximize_button_icon">
  <rectangle color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75" filled="false"
			x="ButtonIPad" y="ButtonIPad" width="width-ButtonIPad*2-1" height="height-ButtonIPad*2-1"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75" width="1"
			x1="ButtonIPad" y1="ButtonIPad+1" x2="width-ButtonIPad" y2="ButtonIPad+1"/>
</draw_ops>

<draw_ops name="maximize_button_icon_unfocused">
 <include name="button_bg_unfocused"/>
		<rectangle color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35" filled="false"
			x="ButtonIPad" y="ButtonIPad" width="width-ButtonIPad*2-1" height="height-ButtonIPad*2-1"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35" width="1"
			x1="ButtonIPad" y1="ButtonIPad+1" x2="width-ButtonIPad" y2="ButtonIPad+1"/>
</draw_ops>

<draw_ops name="maximize_button_normal">
  <include name="button_bg"/>
  <include name="maximize_button_icon"/>
</draw_ops>
<draw_ops name="maximize_button_prelight">
  <include name="button_bg_prelight"/>
  <include name="maximize_button_icon"/>
</draw_ops>
<draw_ops name="maximize_button_pressed">
  <include name="button_bg_pressed"/>
  <include name="maximize_button_icon"/>
</draw_ops>
<draw_ops name="maximize_button_unfocused">
  <include name="button_bg_unfocused"/>
  <include name="maximize_button_icon_unfocused"/>
</draw_ops>

<draw_ops name="normal_window_icon">
		<rectangle color="gtk:bg[NORMAL]" filled="true"
			x="0" y="0" width="width-1" height="height-1"/>
		<rectangle color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75" filled="false"
			x="0" y="0" width="width-1" height="height-1"/>
		<line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75" width="2"
			x1="0" y1="1" x2="width" y2="1"/>
	</draw_ops>

	<draw_ops name="pressed_window_icon">
		<rectangle color="gtk:bg[ACTIVE]" filled="true"
			x="0" y="0" width="width-1" height="height-1"/>
		<rectangle color="blend/gtk:bg[ACTIVE]/gtk:fg[ACTIVE]/0.75" filled="false"
			x="0" y="0" width="width-1" height="height-1"/>
		<line color="blend/gtk:bg[ACTIVE]/gtk:fg[ACTIVE]/0.75" width="2"
			x1="0" y1="1" x2="width" y2="1"/>
	</draw_ops>

	<draw_ops name="prelight_window_icon">
		<rectangle color="gtk:bg[PRELIGHT]" filled="true"
			x="0" y="0" width="width-1" height="height-1"/>
		<rectangle color="blend/gtk:bg[PRELIGHT]/gtk:fg[PRELIGHT]/0.75" filled="false"
			x="0" y="0" width="width-1" height="height-1"/>
		<line color="blend/gtk:bg[PRELIGHT]/gtk:fg[PRELIGHT]/0.75" width="2"
			x1="0" y1="1" x2="width" y2="1"/>
	</draw_ops>

	<draw_ops name="mini_window_icon_unfocused">
		<rectangle color="gtk:bg[INSENSITIVE]" filled="true"
			x="0" y="0" width="width-1" height="height-1"/>
		<rectangle color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35" filled="false"
			x="0" y="0" width="width-1" height="height-1"/>
		<line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35" width="2"
			x1="0" y1="1" x2="width" y2="1"/>
	</draw_ops>

	<draw_ops name="restore_button_normal">
		<include name="button_bg"/>
		<include name="normal_window_icon" 
			x="3 + ButtonIPad" y="ButtonIPad+1" 
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
		<include name="normal_window_icon" 
			x="ButtonIPad" y="3 + ButtonIPad+1"
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
	</draw_ops>

	<draw_ops name="restore_button_pressed">
		<include name="button_bg_pressed"/>
		<include name="pressed_window_icon" 
			x="3 + ButtonIPad" y="ButtonIPad+1" 
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
		<include name="pressed_window_icon" 
			x="ButtonIPad" y="3 + ButtonIPad+1"
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
	</draw_ops>

	<draw_ops name="restore_button_prelight">
		<include name="button_bg_prelight"/>
		<include name="prelight_window_icon" 
			x="3 + ButtonIPad" y="ButtonIPad+1" 
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
		<include name="prelight_window_icon" 
			x="ButtonIPad" y="3 + ButtonIPad+1"
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
	</draw_ops>

	<draw_ops name="restore_button_unfocused">
		<include name="button_bg_unfocused"/>
		<include name="mini_window_icon_unfocused" 
			x="3 + ButtonIPad" y="ButtonIPad+1" 
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
		<include name="mini_window_icon_unfocused" 
			x="ButtonIPad" y="3 + ButtonIPad+1"
			width="width - 7 - ButtonIPad"
			height="height - 7 - ButtonIPad"/>
	</draw_ops>

<!--
<draw_ops name="restore_button_icon">
  <rectangle color="gtk:fg[NORMAL]" filled="false"
             x="ButtonIPad + 2" y="ButtonIPad + 2" width="width-ButtonIPad*2-5" height="height-ButtonIPad*2-5"/>
  <line color="gtk:fg[NORMAL]" width="1"
        x1="ButtonIPad + 3" y1="ButtonIPad + 3" x2="width-ButtonIPad - 3" y2="ButtonIPad + 3"/>
</draw_ops>

<draw_ops name="restore_button_icon_unfocused">
 <rectangle color="blend/gtk:fg[NORMAL]/gtk:bg[NORMAL]/0.7" filled="false"
             x="ButtonIPad + 2" y="ButtonIPad + 2" width="width-ButtonIPad*2-5" height="height-ButtonIPad*2-5"/>
  <line color="blend/gtk:fg[NORMAL]/gtk:bg[NORMAL]/0.7" width="1"
        x1="ButtonIPad + 3" y1="ButtonIPad + 3" x2="width-ButtonIPad - 3" y2="ButtonIPad + 3"/>
</draw_ops>

<draw_ops name="restore_button_normal">
  <include name="button_bg"/>
  <include name="restore_button_icon"/>
</draw_ops>
<draw_ops name="restore_button_prelight">
  <include name="button_bg_prelight"/>
  <include name="restore_button_icon"/>
</draw_ops>
<draw_ops name="restore_button_pressed">
  <include name="button_bg_pressed"/>
  <include name="restore_button_icon_unfocused"/>
</draw_ops>
<draw_ops name="restore_button_unfocused">
  <include name="button_bg_unfocused"/>
  <include name="restore_button_icon_unfocused"/>
</draw_ops>
-->
<draw_ops name="minimize_button_icon">
  <line color="blend/gtk:bg[NORMAL]/gtk:fg[NORMAL]/0.75"
			x1="ButtonIPad"
			y1="height - ButtonIPad - ThickLineWidth + 2"
			x2="width - ButtonIPad"
			y2="height - ButtonIPad - ThickLineWidth + 2"
			width="2"/>
</draw_ops>

<draw_ops name="minimize_button_icon_unfocused">
  <line color="blend/gtk:fg[INSENSITIVE]/gtk:bg[INSENSITIVE]/0.35"
			x1="ButtonIPad"
			y1="height - ButtonIPad - ThickLineWidth + 2"
			x2="width - ButtonIPad"
			y2="height - ButtonIPad - ThickLineWidth + 2"
			width="2"/>
</draw_ops>

<draw_ops name="minimize_button_normal">
  <include name="button_bg"/>
  <include name="minimize_button_icon"/>
</draw_ops>
<draw_ops name="minimize_button_prelight">
  <include name="button_bg_prelight"/>
  <include name="minimize_button_icon"/>
</draw_ops>
<draw_ops name="minimize_button_pressed">
  <include name="button_bg_pressed"/>
  <include name="minimize_button_icon"/>
</draw_ops>
<draw_ops name="minimize_button_unfocused">
  <include name="button_bg_unfocused"/>
  <include name="minimize_button_icon_unfocused"/>
</draw_ops>

<draw_ops name="blank">
<!-- nothing -->
</draw_ops>

<frame_style name="normal" geometry="normal">
  <piece position="entire_background" draw_ops="round_bevel_unfocused"/>
  <piece position="title" draw_ops="title_unfocused"/>
  <button function="close" state="normal" draw_ops="close_button_unfocused"/>
  <button function="close" state="pressed" draw_ops="close_button_pressed"/>
  <button function="close" state="prelight" draw_ops="close_button_prelight"/>
  <button function="maximize" state="normal" draw_ops="maximize_button_unfocused"/>
  <button function="maximize" state="pressed" draw_ops="maximize_button_pressed"/>
  <button function="maximize" state="prelight" draw_ops="maximize_button_prelight"/>
  <button function="minimize" state="normal" draw_ops="minimize_button_unfocused"/>
  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed"/>
  <button function="minimize" state="prelight" draw_ops="minimize_button_prelight"/>
  <button function="menu" state="normal" draw_ops="menu_button_unfocused"/>
  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
</frame_style>

<frame_style name="focused" geometry="normal" parent="normal">
  <piece position="entire_background" draw_ops="round_bevel"/>
  <piece position="title" draw_ops="title"/>
  <button function="close" state="normal" draw_ops="close_button_normal"/>
  <button function="maximize" state="normal" draw_ops="maximize_button_normal"/>
  <button function="minimize" state="normal" draw_ops="minimize_button_normal"/>
  <button function="menu" state="normal" draw_ops="menu_button_normal"/>
</frame_style>

<frame_style name="normal_maximized" geometry="normal_maximized">
  <piece position="entire_background" draw_ops="bevel_maximized_unfocused"/>
  <piece position="title" draw_ops="title_unfocused"/>
  <button function="close" state="normal" draw_ops="close_button_unfocused"/>
  <button function="close" state="pressed" draw_ops="close_button_pressed"/>
  <button function="close" state="prelight" draw_ops="close_button_prelight"/>
  <button function="maximize" state="normal" draw_ops="restore_button_unfocused"/>
  <button function="maximize" state="pressed" draw_ops="restore_button_pressed"/>
  <button function="maximize" state="prelight" draw_ops="restore_button_prelight"/>
  <button function="minimize" state="normal" draw_ops="minimize_button_unfocused"/>
  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed"/>
  <button function="minimize" state="prelight" draw_ops="minimize_button_prelight"/>
  <button function="menu" state="normal" draw_ops="menu_button_unfocused"/>
  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
</frame_style>

<frame_style name="focused_maximized" geometry="normal_maximized" parent="normal_maximized">
  <piece position="entire_background" draw_ops="bevel_maximized"/>
  <piece position="title" draw_ops="title"/>
  <button function="close" state="normal" draw_ops="close_button_normal"/>
  <button function="maximize" state="normal" draw_ops="restore_button_normal"/>
  <button function="minimize" state="normal" draw_ops="minimize_button_normal"/>
  <button function="menu" state="normal" draw_ops="menu_button_normal"/>
</frame_style>

<frame_style name="border" geometry="border" parent="normal">
  <piece position="entire_background" draw_ops="round_bevel_unfocused"/>
  <piece position="title" draw_ops="blank"/>
</frame_style>

<frame_style_set name="normal">
   <frame focus="yes" state="normal" resize="both" style="focused"/>
   <frame focus="no" state="normal" resize="both" style="normal"/>
   <frame focus="yes" state="maximized" style="focused_maximized"/>
   <frame focus="no" state="maximized" style="normal_maximized"/>
   <frame focus="yes" state="shaded" style="focused"/>
   <frame focus="no" state="shaded" style="normal"/>
   <frame focus="yes" state="maximized_and_shaded" style="focused_maximized"/>
   <frame focus="no" state="maximized_and_shaded" style="normal_maximized"/>
</frame_style_set>

<frame_style_set name="utility" parent="normal">
<frame focus="yes" state="normal" resize="both" style="focused"/>
<frame focus="no" state="normal" resize="both" style="normal"/>
<!-- this is a bunch of crack since utility windows shouldn't be maximized -->
<frame focus="yes" state="maximized" style="focused"/>
<frame focus="no" state="maximized" style="normal"/>
<frame focus="yes" state="shaded" style="focused"/>
<frame focus="no" state="shaded" style="normal"/>
<frame focus="yes" state="maximized_and_shaded" style="focused"/>
<frame focus="no" state="maximized_and_shaded" style="normal"/>
</frame_style_set>

<frame_style_set name="border">
<frame focus="yes" state="normal" resize="both" style="border"/>
<frame focus="no" state="normal" resize="both" style="border"/>
<frame focus="yes" state="maximized" style="border"/>
<frame focus="no" state="maximized" style="border"/>
<frame focus="yes" state="shaded" style="border"/>
<frame focus="no" state="shaded" style="border"/>
<frame focus="yes" state="maximized_and_shaded" style="border"/>
<frame focus="no" state="maximized_and_shaded" style="border"/>
</frame_style_set>

<window type="normal" style_set="normal"/>
<window type="dialog" style_set="normal"/>
<window type="modal_dialog" style_set="normal"/>
<window type="menu" style_set="normal"/>
<window type="utility" style_set="normal"/>
<window type="border" style_set="border"/>

<menu_icon function="close" state="normal" draw_ops="close_button_icon_unfocused"/>
<menu_icon function="maximize" state="normal" draw_ops="maximize_button_icon_unfocused"/>
<menu_icon function="unmaximize" state="normal" draw_ops="restore_button_unfocused"/>
<menu_icon function="minimize" state="normal" draw_ops="minimize_button_icon_unfocused"/>

</metacity_theme>
```

---

### Post by dumblebee100 on 2009-08-18
I hoped someone will help me in that little issue ...

but from this I concluded that no one is interested in gtkrc editing ...or else you people fear to edit all the default things ...

Its linux folks ..we have to make our own system ...and share our success with others 

31 views but no reply ....I didnt expect this from ubuntu community

---

### Post by kadde1968 on 2009-09-11
You should put this in 
Main Support Categories > Desktop Environment.
I think they can help you.

---

