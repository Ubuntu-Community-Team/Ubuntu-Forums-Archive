---
title: "HOWTO: Conky Multi-Desktop Configuration."
date: 2011-07-04
forum: General Help
---

### Post by 42dorian on 2011-07-04
I'm doing this just for the sake of doing it.  One place to find the "Latest" solution on this issue.  Unburying it so I can find it easily, and easily get results from people who may want to do some experimenting of their own.

**MULTI-WORKSPACE CONKY!**

A Preface:  This is a bit of code I developed, inspired by someone's question about Compiz.  I don't use it myself, but I did get a buzz out of the inspiration and it has become a, relatively untested, possible future way to solve the "I don't have enough room for all the data I want in Conky" problem many of us have.

To be clear, this is a way to get Conky to display different data, or display differently, on different workspaces in Linux.  It has not been fully tested for every window manager, but I know it works in XFCE4.  

There are two methods currently known:  Compiz and Standard.  I will describe the standard, and show the code for it.  Then, I will do Compiz as a special case.  When push comes to shove, they're the same.

**Standard Method:** 4 Workspaces as example.

In Conky there are three Objects that look at your workspace.  ${desktop}, ${desktop_name}, and ${desktop_number}, which may be variations on the same thing.  It really depends on your window manager.  Gnome, KDE, XFCE4, Enlightenment, and yes Compiz, all call a workspace a specific thing in the code.  Note: I will eventually update the specific requirement for each of these when, one day, someone with each of those window managers eventually tests the code and tells me what works.  For now, I will use ${desktop} as the standard term.  When you, the reader, go to try this it may be different for you.

**Currently known:**
XFCE4 = ${desktop}
Compiz = Special Case, explained below.
Gnome,Fluxbox = ${desktop}==, Gnome and Fluxbox both, when tested, spit out errors if only one = is used.  In fact, the double equal is pretty standard.
KDE = Unknown
Enlightenment = Unknown
Other = Unknown

The goal here is to make Conky decide what workspace is currently being shown, and change how it looks accordingly.  So, you are going to want to know how to use an ${if_match} statement.  Which is really very simple.  When I get to the example of how to decide what workspace, it will be formatted like so:

```

${if_match (Condition)}
<Do Something>
${else}
<Do Something Else>
${endif}

```

It is important to note three things for if_match statements.  One is that the (Condition) won't be in brackets, it will be a conky object, probably something that changes.  It will compare what it has changed to, so it will have an equal/greater than/less than/etc. statement after the Conky Object.  Two is that <Do Something/Else>, much like the (Condition), only means you're going to put all of the code you want in use in place of <Do Something/Else> and not that you need the greater than or less than signs.  It's just a place holder.  And finally that you can have as many if_match statements as you want, nested inside eachother depending on what you're trying to compare, as long as you put an equal number of ${endif} objects at the very end of the structure.  And you'll see that in the workspaces example code.  And now that you understand the Conky object to compare the workspace, and the if_match structure, you can make the two work together to see what Conky should display based on your workspace.

Which is this:  **How to compare your workspace to display specific items in Conky.**

```

${if_match ${desktop}=1}
<Insert All Code You Wish On Desktop 1, As You Want It.>
${else}${if_match ${desktop}=2}
<Insert All Code You Wish On Desktop 2, As You Want It, If you don't want anything, leave this empty.>
${else}${if_match ${desktop}=3}
<Insert All Code You Wish On Desktop 3, As You Want It, If you don't want anything, leave this empty.>
${else}${if_match ${desktop}=4}
<Insert All Code You Wish On Desktop 4, As You Want It, If you don't want anything, leave this empty.>
${else}
${endif}${endif}${endif}${endif}

```

Simple, isn't it?  Here's where it isn't.  You need to write an entire Conky for each of those desktops.  Or, at the very minimum, everything that goes under the TEXT object.  This will make it a very long text file, and you may want to make a comment (# at the start of a line to Comment in Conky) to give you a visual cue as to which section is for what workspace.  Also, as time goes on and I get the chance to get some test results in, the ${desktop} variable may have to be replaced with one of the other two variables (${desktop_name} or ${desktop_number}) in order for the structure to work for you.  In the case of ${desktop_name} it will be replaced with the title or name of that workspace in quotes.  Example:

```

${desktop_name}="main"}

```

When you don't want Conky to display on a particular desktop/workspace, then simply leave the if_match statement in place, and leave the <Everything You Want> part empty.  Empty, as in without that comment.

There will be consequences to this.  As testing goes on, there may be certain window managers that display the outline of Conky, but leave it blank when you have no data inside.  This will be due to the minimum_size environment variable being the same across all desktops/workspaces.  If/when we discover a way around this, making Conky smarter, I will inform you how here.

**Compiz:  The special case, and why it was the inspiration.**

Compiz is special.  So many Linux users know this.  It's all pretty and cool and stuff.  It's 3D and makes that cube thingy that spins, and all that transparency and... okay I don't use Compiz at all.  I don't particularly like it.  But I did find something out about it when a user (jwcalla, whose problem is the inspiration, thus deserves credit.) came to [this thread]("http://ubuntuforums.org/showthread.php?t=281865") with a problem.  Using Compiz, how do you get the different desktop/workspace areas to display different data?  So, in fact Compiz is the first case we had to try any of this code, and has yet another reason to call it "Special", in this case being that it was the original.  

And then we discovered something in the troubleshooting.  When he ran a command (wmctrl) to show how the desktop was being displayed, we were all shown something very unique about the Compiz window manager.  It doesn't have workspaces or desktops.  It has one desktop image, which it gets by taking the number of workspaces you want, and multiplying that by the horizontal resolution you picked for the monitor.  So, instead of 4 workspaces, each, say, 1920x1080, it was one giant workspace that was 7680x1080.  And then it takes that, and wraps it around a 3D object (the Cube you see in so many screenshots) like a tiled mural.  This is why Compiz calls them Viewports.  It's just one narrow view of the mural.

So, how do you make Conky choose from that?  Well, each pseudo-workspace, AKA each side of the cube, AKA Viewport, actually exists at a certain X co-ordinate on the tiled mural.  "Huh?" Yeah, I know.  But wmctrl (you should probably have it on your system, but I can't guarantee it.) has a display readout in a command prompt.  When run using Compiz, the X and Y co-ordinate is shown.  I don't have the program myself, but to run the general readout, you type this in a terminal:

```

wmctrl -d

```

This is important, because this gives us something that has data in the command prompt to **Compare** to.  To get that data, we're going to, and this is my favourite way to say it, grep/awk/sed the hell out of it to narrow down only that spot where we care about the number.  So, we need this command for Conky.  And you'll see it again in the example:

```

 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'

```

Quick explanation:  the | tells the command prompt "before you report what that did, do this." The grep is a search program for command line interfaces that takes what a program spits out, and looks through it for a search string.  awk is a program that reports back a specific result from something you tell it.  sed is stream editor, which takes everything you've been asking the command line and edits or formats it into something you want.

In this case, what this command call is doing is as follows:

wmctrl: desktop report, search for something called 'VP:', report back the second thing you find after you've found 'VP:', take that thing and delete everything that looks like ',0', because I don't need it for what I'm doing.

Guess what.  You just reduced about 5 lines of data about your desktop as it currently is in Compiz, **including it's current horizontal position on the big mural**, down to just a single number for you to compare.  Huzzah!  You just located the number that represents the Viewport you're on!

**How is this useful:**  It's a number.  You can compare to it.  if_match likes that.  And using the ${execi} object, you can tell Conky to do this.

**Getting To The Point!**

For every viewport you have, it will have a number.  Multiply that number by your *Monitor's* horizontal resolution (in this example, 1920 of 1920x1080) and that will be the number you compare the statement to in Conky.  Also in this example, the ${execi} object, which means execute this command, at this interval, is being run every 60 seconds.  Yes, this will mean, it quite possibly could take a delay of a few seconds for Conky to know you're on a different Viewport.

Here's the desktop comparison for Compiz:
```

${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 1920}
(Insert All Code Below The TEXT section that you want on the first viewport.)
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 3840}
(Insert All Code Below The TEXT section that you want on the second viewport.)
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 5760}
(Insert All Code Below The TEXT section that you want on the third viewport.)
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 7680}
(Insert All Code Below The TEXT section that you want on the fourth viewport.)
${else}Out Of Viewports (Or copy/paste more of these.)${endif}${endif}${endif}${endif}

```

As with the standard version, make as many if_match statements as you have viewports, as long as you have the same number of ${endif} objects.

That is the current state of the multi-workspace code as I have it.  I am very much looking for people to test it and get back to me on what they may have had to do to get it to work on their window manager.

---

### Post by 42dorian on 2011-07-05
This is a place-holder post that will eventually discuss the implementation of LUA within the Multi-Desktop setup.  When I have time, this post will be a special supplement Howto for using LUA within the Multi-Desktop code.  For now, it's just a place holder.

For now though, from what I know of LUA (Admittedly not nearly enough to call myself anything other than an Amateur.) I can say that you can use the same structure in LUA as you do in Conky for this setup.  Though, this time you definitely need to know whether you're comparing a number, or a name.  I will use a number as an example, but there will have to be a special format for comparing text.  For now, The code for LUA is as follows:

```

desknum= tonumber(conky_parse(${desktop})
if desknum == 1 then
<LUA Code for desktop 1, depending on what it is.>
else if desknum == 2 then
<LUA Code for desktop 2, depending on what it is.>
else if desknum == 3 then
<LUA Code for desktop 3, depending on what it is.>
else if desknum == 4 then
<LUA Code for desktop 4, depending on what it is.>
else
end

```

Admittedly this seems like it's just the exact same thing as before.  Funny enough, it is.  There are going to be a few variations on this, perhaps a slightly different requirement depending on the way you've got your LUA script set up.  Some methods of coding are more accepting of this simple structure, and others may spit out errors if you use it.  Further testing and examples will still be needed to answer every version.

A note on this:  I'm still looking for a LUA consultant to help me hammer out a better explanation with examples.

---

### Post by stinkeye on 2012-01-12
I am using compiz with 4 viewports ...ie 2 horizontal and 2 vertical
and this is my wmctrl output for unity 11.10.

```
**glen@Oneiric:~$** wmctrl -d
0  * DG: 3360x2100  VP: 0,0  WA: 50,24 1630x1026  N/A
**glen@Oneiric:~$** wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'
*
**glen@Oneiric:~$**
```


This is with 4 horizontal and 1 vertical
```
**glen@Oneiric:~$** wmctrl -d
0  * DG: 6720x1050  VP: 0,0  WA: 50,24 1630x1026  N/A
**glen@Oneiric:~$** wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'
*
**glen@Oneiric:~$**
```

Same result on my 10.04 install.

---

### Post by 42dorian on 2012-01-12
...Very interesting... I'll have to get back to you there.

This is with vertical and horizontal viewports...

Looks like the grep is at fault there.  For reasons unknown, it's not executing the grep.  It's just grabbing the awk and the sed.

Try this instead:

```

wmctrl -d | awk '{print $6}' | sed 's/,0//'

```

And if that does/doesn't work we can figure the two different versions from there.  (Vertical and Horizontal configurations.)

---

### Post by stinkeye on 2012-01-12
This is the output for the 4 viewports
1-2
3-4

```
[COLOR="SeaGreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
0,0
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
1680,0
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
0,1050
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
1680,1050
```


and this is with 4 horizontal
1 2 3 4
```
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
0,0
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
1680,0
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
3360,0
[COLOR="seagreen"]glen@Oneiric:~$[/COLOR] wmctrl -d | awk '{print $6}'
5040,0
```

---

### Post by 42dorian on 2012-01-13
Yes.  It's very easy to get that going then.  Nested if statements.  I'll get to that code later and explain further.  I'm in between some things for now.  I'll just update this post when I get free again.

Thank you stinkeye!  Now, hopefully some others will come along to test KDE and a few other window managers for this too.

You're Compiz with Ubuntu Unity, correct?

---

### Post by stinkeye on 2012-01-13
> **42dorian said:**
> Yes.  It's very easy to get that going then.  Nested if statements.  I'll get to that code later and explain further.  I'm in between some things for now.  I'll just update this post when I get free again.

Thank you stinkeye!  Now, hopefully some others will come along to test KDE and a few other window managers for this too.

You're Compiz with Ubuntu Unity, correct?

Yes using Unity/compiz 11.10.
This was very useful.
There used to be a plugin for older versions of compiz to display your desktop number.
I can now achieve this using conky and the wmctrl command.
As I only use two desktops it was fairly easy by adding...
```
${if_match ${exec wmctrl -d | awk '{print $6}' | sed 's/,0//'} == 1680}${color}DESK 2${else}DESK 1${endif}
```

---

### Post by arclance on 2012-01-15
${desktop} returns numbers (1, 2, 3, 4, etc.) when using [Fluxbox]("http://fluxbox.org/") in Ubuntu 11.04.
So your standard method works with one modification in Fluxbox.
You need to use ${desktop}==1 instead of ${desktop}=1.
== is the normal comparison operator in programing languages because = is used for assignment operations, so this makes sense.

It is also consistent with the [conky documentation]("http://conky.sourceforge.net/variables.html") for ${if_match}.
```

Evaluates the given boolean expression, printing everything between $if_match and 
the matching $endif depending on whether the evaluation returns true or not. Valid
expressions consist of a left side, an operator and a right side. Left and right sides are
being parsed for contained text objects before evaluation. Recognised left and right side
types are:

[LIST]
[*]**double** -      Argument consists of only digits and a single dot.
[*]**long** -         Argument consists of only digits.
[*]**string** -       Argument is enclosed in quotation marks (")
[/LIST]
[COLOR=Red]Valid operands are: '>', '<', '>=','<=', '==','!='.[/COLOR]

```Here is the code I used for a test.
```

${if_match ${desktop}==1}
Workspace 1!
${else}${if_match ${desktop}==2}
Workspace 2!
${else}${if_match ${desktop}==3}
Workspace 3!
${else}${if_match ${desktop}==4}
Workspace 4!
${else}
${endif}${endif}${endif}${endif}

```

---

### Post by mrpeachy on 2012-01-15
had an idea, realised it wouldn't work :)

---

### Post by mrpeachy on 2012-01-15
getting different lua displays on different conkies...
i think having one humongous script containing multiple setups based on if's is not necessary...
(unless you were just using a single script and only wanting to feed the script different settings, but then you would have to go script by script to get the if's in the right place)

the first thing that comes to mind would be along these lines

```

lua_load script1
lua_load script2
lua_load script3

TEXT
if_match 1
${lua main_function1}
else if_match 2
${lua main_function2}
else if_match 3
${lua main_function3}
endif endif endif

```i dont ever use more than one screen, so i havnt tested this

---

### Post by arclance on 2012-01-15
@mrpeachy

That seems like the best way to do it to me too.
Sounds like the right advice for non-LUA scripts as well.

I have 3 monitors with the center one shared with a KVM switch between two computers and the other two each connected to one of the computers.
I am only using ${desktop} right now so I know what workspace I am in on each computer when the center monitor is showing a different computer than the monitor the conky is on.

---

### Post by 42dorian on 2012-01-15
> **arclance said:**
> ${desktop} returns numbers (1, 2, 3, 4, etc.) when using [Fluxbox]("http://fluxbox.org/") in Ubuntu 11.04.
So your standard method works with one modification in Fluxbox.
You need to use ${desktop}==1 instead of ${desktop}=1.
== is the normal comparison operator in programing languages because = is used for assignment operations, so this makes sense.

It is also consistent with the [conky documentation]("http://conky.sourceforge.net/variables.html") for ${if_match}.
```

Evaluates the given boolean expression, printing everything between $if_match and 
the matching $endif depending on whether the evaluation returns true or not. Valid
expressions consist of a left side, an operator and a right side. Left and right sides are
being parsed for contained text objects before evaluation. Recognised left and right side
types are:

[LIST]
[*]**double** -      Argument consists of only digits and a single dot.
[*]**long** -         Argument consists of only digits.
[*]**string** -       Argument is enclosed in quotation marks (")
[/LIST]
[COLOR=Red]Valid operands are: '>', '<', '>=','<=', '==','!='.[/COLOR]

```Here is the code I used for a test.
```

${if_match ${desktop}==1}
Workspace 1!
${else}${if_match ${desktop}==2}
Workspace 2!
${else}${if_match ${desktop}==3}
Workspace 3!
${else}${if_match ${desktop}==4}
Workspace 4!
${else}
${endif}${endif}${endif}${endif}

```

Excellent, thank you arclance!  I shall append the known window managers in the howto to include Fluxbox.  Indeed, it is nice to know it uses the standard comparison operator.  XFCE4 (MY standard Window Manager) just needs the one equal sign to get it to work.  So, I thank you immensely for testing an alternate for me.

@mrpeachy, I figured you'd step in on this one.  As you know rather well, I'm not all-knowing of the ways of LUA.  I only have very basic stuff in my repertoire.

Question though.  Are you referring to changing which **functions** in Lua are displayed in Conky, depending on which workspace you're on?  Or are you referring to changing what the already loaded functions do depending on which workspace you're on?

The way I see it working, this Multi-Desktop thing, is that in order to get everything to line up properly every time, the entire script you want there in that workspace has to be lined up in a single if_match case.  You don't want every little section that changes to be making it's own decisions, you want the entire script to be run at once when the desktop/workspace/veiwport/whatever your WM Calls It changes or is different.

In LUA, if you don't want one element of the function to run, you leave an "if desknum==x" wrapped around it so it doesn't run unless that's there.  I know, however, that certain functions may or may not like that.  Hence why I need a LUA consultant on this.

---

### Post by arclance on 2012-01-15
> **42dorian said:**
> Excellent, thank you arclance!  I shall append the known window managers in the howto to include Fluxbox.  Indeed, it is nice to know it uses the standard comparison operator.  XFCE4 (MY standard Window Manager) just needs the one equal sign to get it to work.  So, I thank you immensely for testing an alternate for me.

Your welcome.
Out of curiosity what happens if you try ${desktop}== in XFCE4?

I will also give you some advice on conky if statements that I have not seen mentioned anywhere else.
When using ${if_running} I discovered that if you want to insert blank lines with an if statement in conky each line must have at least one space on it or conky ignores them.

---

### Post by 42dorian on 2012-01-16
> **arclance said:**
> Your welcome.
Out of curiosity what happens if you try ${desktop}== in XFCE4?

I will also give you some advice on conky if statements that I have not seen mentioned anywhere else.
When using ${if_running} I discovered that if you want to insert blank lines with an if statement in conky each line must have at least one space on it or conky ignores them.

In XFCE4 it accepts one or two equal signs with no difference.  ACTUAL operations require the double equal, but not for the ${desktop} variable apparently.

You haven't seen it mentioned anywhere because, really, no one uses an If statement in that way.  It hasn't been used, so it hasn't really come up before.  In the case of the Multi-Desktop setup, there may well be desktops where you don't want Conky at all, and having absolutely nothing in the If statement for that workstation, although it hasn't been tested on every window manager yet, may well just turn Conky off.  Leaving either nothing on that desktop, Or, as I theorise, it will leave an empty square/rectangle where Conky would be.

---

### Post by djyoung4 on 2012-01-20
```
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 0,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 1280,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 2560,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 3840,0  WA: 0,1 1280x799  Workspace 1

```
heres my smctrl -d.  workin on the different viewports
ok I get this error on gnome
```
jyoung4@Daniels-computer:~$ conky -c ~/.conkyrc2
Conky: forked to background, pid is 3342
djyoung4@Daniels-computer:~$ 
Conky: desktop window (1e000a9) is subwindow of root window (ad)
Conky: drawing to desktop window
Conky: drawing to double buffer
Conky: Bad arguments: '* ' and ' 1280'
Conky: compare failed for expression '* == 1280'
Conky: Bad arguments: '* ' and ' 1280'
Conky: compare failed for expression '* == 1280'

```
heres my code
```
# Conky sample configuration
#USAZ0233, USHI0026
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Deja Vu Sans Mono:size=18

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Maximum width
maximum_width 10000

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color black
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment top_middle
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address
  #-d DATATYPE, --datatype=DATATYPE
                        #[default: HT] The data type options are: DW (Day of
                        #Week), WF (Weather Font output), WI (Weather Icon
                        #Path), LT (Forecast:Low Temp,Current:Feels Like Temp),
                        #HT (Forecast:High Temp,Current:Current Temp), CC
                        #(Current Conditions), CT (Conditions Text), PC
                        #(Precipitation Chance), HM (Humidity), VI
                        #(Visibility), WD (Wind Direction), WA (Wind Angle - in
                        #degrees), WS (Wind Speed), WG (Wind Gusts), BF
                        #(Bearing Font), BI (Bearing Icon Path), BS (Bearing
                        #font with Speed), CN (City Name), CO (Country), OB
                        #(Observatory), SR (SunRise), SS (SunSet), DL
                        #(DayLight), MP (Moon Phase), MF (Moon Font), MI (Moon
                        #Icon Path), BR (Barometer Reading), BD (Barometer
                        #Description), UI (UV Index), UT (UV Text), DP (Dew
                        #Point), LU (Last Update at weather.com), LF (Last
                        #Fetch from weather.com). Not applicable at command
                        #line when using templates.


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
# -- Lua Load -- #

TEXT
${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 1280}
${cpubar cpu1}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 2560}
${cpubar cpu2}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 3840}
${cpubar cpu0}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 5120}
${cpu cpu1}
${else}${endif}${endif}${endif}${endif}
```

---

### Post by 42dorian on 2012-01-20
> **djyoung4 said:**
> ```
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 0,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 1280,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 2560,0  WA: 0,1 1280x799  Workspace 1
djyoung4@Daniels-computer:~$ wmctrl -d
0  * DG: 5120x800  VP: 3840,0  WA: 0,1 1280x799  Workspace 1

```
heres my smctrl -d.  workin on the different viewports
ok I get this error on gnome
```
jyoung4@Daniels-computer:~$ conky -c ~/.conkyrc2
Conky: forked to background, pid is 3342
djyoung4@Daniels-computer:~$ 
Conky: desktop window (1e000a9) is subwindow of root window (ad)
Conky: drawing to desktop window
Conky: drawing to double buffer
Conky: Bad arguments: '* ' and ' 1280'
Conky: compare failed for expression '* == 1280'
Conky: Bad arguments: '* ' and ' 1280'
Conky: compare failed for expression '* == 1280'

```
heres my code
```
# Conky sample configuration
#USAZ0233, USHI0026
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Deja Vu Sans Mono:size=18

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Maximum width
maximum_width 10000

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color black
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment top_middle
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address
  #-d DATATYPE, --datatype=DATATYPE
                        #[default: HT] The data type options are: DW (Day of
                        #Week), WF (Weather Font output), WI (Weather Icon
                        #Path), LT (Forecast:Low Temp,Current:Feels Like Temp),
                        #HT (Forecast:High Temp,Current:Current Temp), CC
                        #(Current Conditions), CT (Conditions Text), PC
                        #(Precipitation Chance), HM (Humidity), VI
                        #(Visibility), WD (Wind Direction), WA (Wind Angle - in
                        #degrees), WS (Wind Speed), WG (Wind Gusts), BF
                        #(Bearing Font), BI (Bearing Icon Path), BS (Bearing
                        #font with Speed), CN (City Name), CO (Country), OB
                        #(Observatory), SR (SunRise), SS (SunSet), DL
                        #(DayLight), MP (Moon Phase), MF (Moon Font), MI (Moon
                        #Icon Path), BR (Barometer Reading), BD (Barometer
                        #Description), UI (UV Index), UT (UV Text), DP (Dew
                        #Point), LU (Last Update at weather.com), LF (Last
                        #Fetch from weather.com). Not applicable at command
                        #line when using templates.


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
# -- Lua Load -- #

TEXT
${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 1280}
${cpubar cpu1}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 2560}
${cpubar cpu2}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 3840}
${cpubar cpu0}
${else}${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $2}' | sed 's/,0//'} == 5120}
${cpu cpu1}
${else}${endif}${endif}${endif}${endif}
```

Yeah.  Same as the last example.  You need to change to '{print $6}' to grab your particular viewport.

---

### Post by djyoung4 on 2012-01-20
> **42dorian said:**
> Yeah.  Same as the last example.  You need to change to '{print $6}' to grab your particular viewport.
no errors now but no display

---

### Post by 42dorian on 2012-01-20
> **djyoung4 said:**
> no errors now but no display

Right.  Flip viewports a couple times.

*EDIT*  In fact, do two things.  Change the maximum_size variable to something like 400 instead of 10000, and flip to the FOURTH Viewport.  A maximum width of 10000 could very well put all results on the fourth viewport over.  Just, play it safe and limit it to around 400.  Or, leave one of those ifs blank to see if one of the viewports is blank.

---

### Post by djyoung4 on 2012-01-20
> **42dorian said:**
> Right.  Flip viewports a couple times.

*EDIT*  In fact, do two things.  Change the maximum_size variable to something like 400 instead of 10000, and flip to the FOURTH Viewport.  A maximum width of 10000 could very well put all results on the fourth viewport over.  Just, play it safe and limit it to around 400.  Or, leave one of those ifs blank to see if one of the viewports is blank.
ok so i changed it to max width 400 and the code for viewport 2 goes to viewport 3 and the code for viewport 3 goes to viewport 4.  I get no display on 1 and 2
```
# Conky sample configuration
#USAZ0233, USHI0026
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Deja Vu Sans Mono:size=18

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Maximum width
maximum_width 400

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color black
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment top_middle
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address
  #-d DATATYPE, --datatype=DATATYPE
                        #[default: HT] The data type options are: DW (Day of
                        #Week), WF (Weather Font output), WI (Weather Icon
                        #Path), LT (Forecast:Low Temp,Current:Feels Like Temp),
                        #HT (Forecast:High Temp,Current:Current Temp), CC
                        #(Current Conditions), CT (Conditions Text), PC
                        #(Precipitation Chance), HM (Humidity), VI
                        #(Visibility), WD (Wind Direction), WA (Wind Angle - in
                        #degrees), WS (Wind Speed), WG (Wind Gusts), BF
                        #(Bearing Font), BI (Bearing Icon Path), BS (Bearing
                        #font with Speed), CN (City Name), CO (Country), OB
                        #(Observatory), SR (SunRise), SS (SunSet), DL
                        #(DayLight), MP (Moon Phase), MF (Moon Font), MI (Moon
                        #Icon Path), BR (Barometer Reading), BD (Barometer
                        #Description), UI (UV Index), UT (UV Text), DP (Dew
                        #Point), LU (Last Update at weather.com), LF (Last
                        #Fetch from weather.com). Not applicable at command
                        #line when using templates.


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
# -- Lua Load -- #

TEXT
${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $6}' | sed 's/,0//'} == 1280}
${cpubar cpu1}
${else}${if_match ${execi 6 wmctrl -d | grep 'VP:' | awk '{print $6}' | sed 's/,0//'} == 2560}
${color red}${cpubar cpu2}
${else}${if_match ${execi 6 wmctrl -d | grep 'VP:' | awk '{print $6}' | sed 's/,0//'} == 3840}
${color blue}${cpubar cpu0}
${else}${if_match ${execi 6 wmctrl -d | grep 'VP:' | awk '{print $6}' | sed 's/,0//'} == 5120}
${color white}${cpu cpu1}
${else}${endif}${endif}${endif}${endif}
```

---

### Post by mrpeachy on 2012-01-25
> **42dorian said:**
> 
@mrpeachy, I figured you'd step in on this one.  As you know rather well, I'm not all-knowing of the ways of LUA.  I only have very basic stuff in my repertoire.

Question though.  Are you referring to changing which **functions** in Lua are displayed in Conky, depending on which workspace you're on?  Or are you referring to changing what the already loaded functions do depending on which workspace you're on?

The way I see it working, this Multi-Desktop thing, is that in order to get everything to line up properly every time, the entire script you want there in that workspace has to be lined up in a single if_match case.  You don't want every little section that changes to be making it's own decisions, you want the entire script to be run at once when the desktop/workspace/veiwport/whatever your WM Calls It changes or is different.

In LUA, if you don't want one element of the function to run, you leave an "if desknum==x" wrapped around it so it doesn't run unless that's there.  I know, however, that certain functions may or may not like that.  Hence why I need a LUA consultant on this.

well usually one lua script has one main function  conky_something
all the other functions you find in a lua script are then in addition to that, but it is the conky_something function that is executed by conky each cycle

so say you had wlourfs bars etc script and you want to use it with 2 differeny conkies with each conky having a different display.... 

you could have just one instance of that script saved and then try and edit it in such a way to add if statements surrounding 2 different settings tables,

 you have conky on one desktop, the script gets fed one lot of settings, you have conky on another desktop the script gets the other set

the problem is first any editing if a script like that by somone who isnt all that well versed in what the script does could easily break it, and second, you might be able to figure out where to put the if's but go to another script and it will be entirely different

OR

you could have 2 versions of the script saves

bars1.lua and bars2.lua set up as you want them... load them both above TEXT
then have which one is executed controlled by the conky if_matches
you would still need to edit the lua scripts to make the names of the main functions different
in bars1.lua --> function conky_main1()
in bars2.lua--> function conky_main2()

---

### Post by 42dorian on 2012-01-26
> **mrpeachy said:**
> well usually one lua script has one main function  conky_something
all the other functions you find in a lua script are then in addition to that, but it is the conky_something function that is executed by conky each cycle

so say you had wlourfs bars etc script and you want to use it with 2 differeny conkies with each conky having a different display.... 

you could have just one instance of that script saved and then try and edit it in such a way to add if statements surrounding 2 different settings tables,

 you have conky on one desktop, the script gets fed one lot of settings, you have conky on another desktop the script gets the other set

the problem is first any editing if a script like that by somone who isnt all that well versed in what the script does could easily break it, and second, you might be able to figure out where to put the if's but go to another script and it will be entirely different

OR

you could have 2 versions of the script saves

bars1.lua and bars2.lua set up as you want them... load them both above TEXT
then have which one is executed controlled by the conky if_matches
you would still need to edit the lua scripts to make the names of the main functions different
in bars1.lua --> function conky_main1()
in bars2.lua--> function conky_main2()

That second way sounds... sloppy... Am I missing something that makes it fall into place?

The way I understand LUA (Admittedly very little, overall) I don't think that it would make any sense to have entirely different LUA scripts for different desktops/workspaces/viewports.  Having one script that changes depending on which desktop/workspace/viewport is showing makes more sense.  You program a set of, say, rings, or bars, or text objects.  Let's say you have 5 of them in one function, all showing on a Desktop/Etc.  When it goes to Desktop/Etc. 2, 3, 4, etc. ring/bar/object 1 follows settings for Desktop 1 including colour, size, position, rotation, even what it shows (Filesystem size/CPU Usage/RAM/Whatever.) and all of those settings change when on Desktop/Etc. 2.  Even to the point that some of said Rings/Bars/Etc. have no settings at all for Desktops/Etc. they aren't needed for.

Am I communicating the first idea you had there, or something completely different/insane?  Just in the hopes we're squawking the same gibberish here.

---

### Post by mrpeachy on 2012-01-26
^ that is in line with my first suggestion

however, you are trying to write a guide on how people can set up conky on different desktops
and unless you are going to specify for every lua script they might want to use, where they need to put in the IF's and ends, its going to be difficult to get it right

but you can say

save different configurations as different file names
locate function conky_ in each file and edit so that each one is unique
load all lua scripts above TEXT
call functions as needed below TEXT

and it should work no matter what lua script is

---

### Post by Lateralus138 on 2012-09-25
Hello I am running Ubuntu 12.04 with Unity/Compiz and It's not working correctly. Here's the wmctrl -d:
```
0  * DG: 5464x768  VP: 0,0  WA: 0,24 1366x744  N/A
```

Here's my script TEXT:
```
TEXT
${if_match ${execi 60 wmctrl -d | grep 'VP:' | awk '{print $6}' | sed 's/,0//'} == 1366}
#${image ~/Pictures/conky.png -p- 1,14 -s 278x436}
#${image /usr/share/unity/5/launcher_bfb.png -p 215,10 -s 48x48}
${image ~/Pictures/coc.jpg -p 222,16 -s 36x40}
$sysname $kernel on $machine
${execi 300 ~/bin/weather.sh 27393_pc}          ${font Antipasto}${time %H : %M : %S}${font}
Misc... ${hr 2}
    Hostname $alignr Ian's $nodename
    Uptime $alignr $uptime
    Load $alignr $loadavg
#CPU $alignr ${cpu cpu0}% ${cpu cpu1}%
#${cpubar cpu0}
#${cpubar cpu1}
#RAM $alignc $mem / $memmax $alignr $memperc%
#$membar
#/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
#${fs_bar /}
Processes ${hr 2}    
$processes processes ($running_processes running)
    NAME $alignr PID   CPU   MEM
    ${hr 1}   
    ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}
    ${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
    ${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
    ${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
    ${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}
    ${top name 6} $alignr ${top pid 6} ${top cpu 6} ${top mem 6}

CPU Graphs ${hr 2}
 1  ${cpugraph cpu0 00ff00 ff0000}
 2  ${cpugraph cpu1 ff0000 00ff00}
Network ${hr 2}
    Inbound $alignr ${downspeed wlan0} kb/s
    ${downspeedgraph wlan0 33ffcc 00ff00}
    Outbound $alignr ${upspeed wlan0} kb/s
    ${upspeedgraph wlan0 ffcc00 ff00ff}
    Upload: ${alignr}${totalup wlan0}
    Download: ${alignr}${totaldown wlan0}
${else}
${endif}
```

---

### Post by stinkeye on 2012-09-26
> **Lateralus138 said:**
> Hello I am running Ubuntu 12.04 with Unity/Compiz and It's not working correctly. Here's the wmctrl -d:
```
0  * DG: 5464x768  VP: 0,0  WA: 0,24 1366x744  N/A
```

Here's my script TEXT:
<snip>
I could never get this to work consistently.

Because compiz sees your desktop as one virtual desktop no matter how many workspaces you have you can just increase your **gap_x** setting to move to another workspace.
If you just want to start a particular conky on workspace 2,remove the **if_match** statement, and in the config above TEXT" use...
```
gap_x 1366
```
Increase 1366 to move it in from the left edge on workspace 2

The config must also use
```
alignment tl
own_window_type **normal**
own_window_hints undecorated,below,skip_taskbar,skip_pager
```
...making sure to remove **sticky** from own_window_hints.

*own_window_type **override** ignores own_window_hints.

---

### Post by Lateralus138 on 2012-09-26
^ Perfect, thanx a lot I have everything exactly where I want it now.

---

