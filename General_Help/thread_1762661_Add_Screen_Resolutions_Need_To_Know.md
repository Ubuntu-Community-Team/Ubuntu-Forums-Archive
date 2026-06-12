---
title: "Add Screen Resolutions Need To Know"
date: 2011-05-19
forum: General Help
---

### Post by Dracolver on 2011-05-19
ok, so basically I want to change the resolution on my computer as the desktop is partially lost off of the screen.  The needed resolution is not available so I am attempting to add a new resolution.  I have used the url  [https://wiki.kubuntu.org/X/Config/Resolution](https://wiki.kubuntu.org/X/Config/Resolution)  for information on how to do this.  I am COMPLETELY new to Ubuntu and entering code so a TON of the results online have meant jibberish to me as people leave out the basics which I cannot find.   Here is what I've done so far in the terminal...

**I enter:**
xrandr

**I get:**
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1920x1080      60.0*+
   1920x1080i     30.0  
   1280x720       60.0  
  2020x1180_60.00 (0x169)  200.0MHz
        h: width  2024 start 2160 end 2376 total 2728 skew    0 clock   73.3KHz
        v: height 1180 start 1183 end 1193 total 1224           clock   59.9Hz

**I enter:**
xrandr --newmode <Mode``Line>

**I get:**
bash: syntax error near unexpected token `newline'
[B]
Already I see an error message though without knowing what else to do I try to continue the code as follows...[/B]

**I enter:**
cvt 2020 1180

**I get:**
# 2024x1180 59.90 Hz (CVT) hsync: 73.31 kHz; pclk: 200.00 MHz
Modeline "2024x1180_60.00"  200.00  2024 2160 2376 2728  1180 1183 1193 1224 -hsync +vsync

[B]At this point I see it shows 2024x1180 when I actually entered 2020x1180 which I find odd, though I try the next part with both 2024 and 2020 with same results.
[/B]
**I enter:**
xrandr --newmode "2020x1180_60.00"  200.00  2024 2160 2376 2728  1180 1183 1193 1224 -hsync +vsync

**I normally get no response after with a blank cursor, though_ one time_ I got:**
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27
[B]
 I am having major difficulty with this and I would greatly appreciate anyones help on this, truly!


[/B]

---

### Post by jerrrys on 2011-05-20
looks like your on the right path.  
try this 'how to'.  its the same thing, just easier to follow

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

