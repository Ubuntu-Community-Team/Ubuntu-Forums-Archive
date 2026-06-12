---
title: "tint2 configuration"
date: 2009-08-26
forum: General Help
---

### Post by m_ad on 2009-08-26
I'm trying to round off the corners of my tint2 panel. I have a taskbar, system tray, battery applet and clock. When I specify the roundness, then set the systray, battery applet and clock to use that roundness, I have 4 rounded panels.

Is there a way to make it look like one big panel, and round only the leftmost/rightmost corners?

My tint2rc:
```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------
# For more information about tint2, see:
# http://code.google.com/p/tint2/wiki/Welcome
#
# For more config file examples, see:
# http://crunchbanglinux.org/forums/topic/3232/my-tint2-config/
#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
# The whole row
rounded = 8
border_width = 0
background_color = #FFFFFF 20
border_color = #FFFFFF 30

# Active taskbar item
rounded = 6
border_width = 1
background_color = #FFFFFF 20
border_color = #FFFFFF 20

# Inactive taskbar item
rounded = 6
border_width = 1
background_color = #FFFFFF 20
border_color = #FFFFFF 0

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom center
panel_size = 88% 25
panel_margin = 0 3
panel_padding = 0 0 0
font_shadow = 0
panel_background_id = 0

#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = single_desktop
taskbar_padding = 3 3 3
taskbar_background_id = 1

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 200
task_centered = 0
task_padding = 2 2
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 0 0
systray_background_id = 1

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %l:%M %P
time1_font = sans 7
time2_format = %A, %B %d
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 4 6
clock_background_id = 1

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 1
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 1


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

---

### Post by mcduck on 2009-08-26
Try this:

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------
# For more information about tint2, see:
# http://code.google.com/p/tint2/wiki/Welcome
#
# For more config file examples, see:
# http://crunchbanglinux.org/forums/topic/3232/my-tint2-config/
#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
# The whole row
rounded = 8
border_width = 0
background_color = #FFFFFF 20
border_color = #FFFFFF 30

# Active taskbar item
rounded = 6
border_width = 1
background_color = #FFFFFF 20
border_color = #FFFFFF 20

# Inactive taskbar item
rounded = 6
border_width = 1
background_color = #FFFFFF 20
border_color = #FFFFFF 0

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom center
panel_size = 88% 25
panel_margin = 0 3
panel_padding = 0 0 0
font_shadow = 0
panel_background_id = 1

#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = single_desktop
taskbar_padding = 3 3 3
taskbar_background_id = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 200
task_centered = 0
task_padding = 2 2
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 0 0
systray_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %l:%M %P
time1_font = sans 7
time2_format = %A, %B %d
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 4 6
clock_background_id = 0

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 1
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

---

### Post by mcduck on 2009-08-26
The only change I did was change the panel's background to "1", and then used "0" for the things you had used "1". Now the rounded background is used for the panel itself, while panel items have no background at all..

---

