---
title: "gconf-editor (apps/metacity/general) button_layout"
date: 2010-09-13
forum: General Help
---

### Post by tbrminsanity on 2010-09-13
What are all the options available for the button layout?
I know the following already:
[LIST]
[*]menu = brings up the window menu
[*]minimize = minimizes the window to the taskbar
[*]maximize = makes the window full screen or windowed
[*]close = closes the window
[*]spacer = puts space between entries
[/LIST]

Is there an option to raise or lower a window?  Is there an option to keep a windows on top?  Is there an option to have a window keep to the current active desktop?

---

### Post by DavidBiesack on 2011-04-01
Your post is kind of old, but I just started using this and had the same question.

I was able to enter the value

  lower

for action_right_click_titlebar

However,  raise_or_lower did not work, even though that is an operation available in /apps/metacity/window_keybindings .  Too bad the [Metacity Documentation]("https://help.ubuntu.com/community/Metacity#General Settings") does not list all the valid values

---

