---
title: "X sever goes wacky after screen orientation changes"
date: 2010-04-03
forum: General Help
---

### Post by hurdevan on 2010-04-03
I created this script that changes to screen orientation when the you tilt the computer(Just for the heck of it). I can detect the tilt with the use of an accelerometer in my laptop. I use the command 'xrandr -o <option>' to change the orientation from my script. 

It works fine the first change but after is tries to change the screen back to normal then the X server goes a little wacky.

What I would like to know is if there is a way to kinda refresh the X server after each orientation change????


Help would be wonderful even though I will probably break my computer showing people that my computer can do what the Ipod Touches do. 

Thanks All.

---

### Post by mcoleman44 on 2010-04-03
Can you describe wacky? Are you using Compiz? Because compiz doesnt support rotation.

---

### Post by hurdevan on 2010-04-03
Hey thanks that did the trick. Although Compiz does work with the orientation changed. I guess it has trouble recovering after you change the screen orientation.

So I guess I could restart Compiz or something but that is still a little inconvenient???

Thanks.

---

### Post by mcoleman44 on 2010-04-03
In your script add this before the rotation.
metacity --replace &
sleep 3s

and after the rotation
compiz --replace

See if that fixes it.

---

### Post by hurdevan on 2010-04-03
> In your script add this before the rotation.
metacity --replace & sleep 3s

and after the rotation
compiz --replace

See if that fixes it. 

Ok I tried that and it had no effect except erring out.
I'm just going to have to live with what I got. Its not like I am going to be using it all that much. Its more of a proof-of-concept.

Thanks.

---

### Post by mcoleman44 on 2010-04-03
Ok, if you ever want it to work, just post the script your using and we can ix it real quick.

---

### Post by hurdevan on 2010-04-03
TU-DU

```

#!/usr/bin/perl

$sys_file = "cat /sys/devices/platform/hdaps/position";



y1:
$line = `$sys_file`;

print $line."\n";
#for($i =0;$i < 500;$i++){}
sleep .500;
@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;
if($L != 1 ){if ($x > 340 and $x < 370 and $y > 610 and $y < 630)
{print "Left\n".$line."\n"; $L = 1;$R = 0;$N = 0;$I = 0;right();}}

if($R != 1 ){if ($x > 640 and $x < 660 and $y > 590 and $y < 610)
{print "Right\n".$line."\n"; $R = 1;$L = 0;$N = 0; $I = 0; left();}}

if($N != 1 ){if ($x > 490 and $x < 510 and $y > 610 and $y < 630)
{print "Normal\n".$line."\n"; $N = 1;$L = 0;$R = 0;$I = 0; normal();}}

if($I != 1 ){if ($x > 490 and $x < 510 and $y > 490 and $y < 510)
{print "Inverted\n".$line."\n"; $I = 1;$L = 0;$R = 0;$N = 0;inverted();}}
goto y1;

sub right{
#`lcd-off`;
#`metacity --replace & sleep 3s`;
`xrandr -o right`;
#`compiz --replace`;
#`lcd-on`;
}
sub left {
#`lcd-off`;
#`metacity --replace & sleep 3s`;
`xrandr -o left`;
#`compiz --replace`;
#`lcd-on`;
}
sub normal {
#`lcd-off`;
#`metacity --replace & sleep 3s`;
`xrandr -o normal`;
#`compiz --replace`;
#`lcd-on`;
}

sub inverted {
#`lcd-off`;
#`metacity --replace & sleep 3s`;
`xrandr -o inverted`;
#`compiz --replace`;
#`lcd-on`;
}


@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;

if($x < $oldx - 5){$xstat = "left\n"}
if($x > $oldx + 5){$xstat = "right\n"}
if($y < $oldy - 5){$ystat = "down\n"}
if($y > $oldy + 5){$ystat = "up\n"}


if($xstat != 99){
if($x - $oldx > $y - $oldy){print $xstat;}
$xstat = 99;
}


if($ystat != 99){
if($x - $oldx < $y - $oldy){print $ystat;} 
$ystat = 99;
}
$oldx = $x;
$oldy = $y;

#print $x."-".$y."\n";
#for($i =0;$i < 500;$i++){}
sleep 1;
goto y1;

```

---

### Post by mcoleman44 on 2010-04-03
```
#!/usr/bin/perl

$sys_file = "cat /sys/devices/platform/hdaps/position";



y1:
$line = `$sys_file`;

print $line."\n";
#for($i =0;$i < 500;$i++){}
sleep .500;
@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;
if($L != 1 ){if ($x > 340 and $x < 370 and $y > 610 and $y < 630)
{print "Left\n".$line."\n"; $L = 1;$R = 0;$N = 0;$I = 0;right();}}

if($R != 1 ){if ($x > 640 and $x < 660 and $y > 590 and $y < 610)
{print "Right\n".$line."\n"; $R = 1;$L = 0;$N = 0; $I = 0; left();}}

if($N != 1 ){if ($x > 490 and $x < 510 and $y > 610 and $y < 630)
{print "Normal\n".$line."\n"; $N = 1;$L = 0;$R = 0;$I = 0; normal();}}

if($I != 1 ){if ($x > 490 and $x < 510 and $y > 490 and $y < 510)
{print "Inverted\n".$line."\n"; $I = 1;$L = 0;$R = 0;$N = 0;inverted();}}
goto y1;

sub right{
`metacity --replace`;    
#`lcd-off`;
`xrandr -o right`;
`compiz --replace`;
#`lcd-on`;
}
sub left {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o left`;
`compiz --replace`;
#`lcd-on`;
}
sub normal {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o normal`;
`compiz --replace`;
#`lcd-on`;
}

sub inverted {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o inverted`;
`compiz --replace`;
#`lcd-on`;
}


@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;

if($x < $oldx - 5){$xstat = "left\n"}
if($x > $oldx + 5){$xstat = "right\n"}
if($y < $oldy - 5){$ystat = "down\n"}
if($y > $oldy + 5){$ystat = "up\n"}


if($xstat != 99){
if($x - $oldx > $y - $oldy){print $xstat;}
$xstat = 99;
}


if($ystat != 99){
if($x - $oldx < $y - $oldy){print $ystat;} 
$ystat = 99;
}
$oldx = $x;
$oldy = $y;

#print $x."-".$y."\n";
#for($i =0;$i < 500;$i++){}
sleep 1;
goto y1;

```

Ok, see if this helps. It might not, but just an idea.

---

### Post by mcoleman44 on 2010-04-03
If the above didnt work then try this.

```
#!/usr/bin/perl

$sys_file = "cat /sys/devices/platform/hdaps/position";



y1:
$line = `$sys_file`;

print $line."\n";
#for($i =0;$i < 500;$i++){}
sleep .500;
@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;
if($L != 1 ){if ($x > 340 and $x < 370 and $y > 610 and $y < 630)
{print "Left\n".$line."\n"; $L = 1;$R = 0;$N = 0;$I = 0;right();}}

if($R != 1 ){if ($x > 640 and $x < 660 and $y > 590 and $y < 610)
{print "Right\n".$line."\n"; $R = 1;$L = 0;$N = 0; $I = 0; left();}}

if($N != 1 ){if ($x > 490 and $x < 510 and $y > 610 and $y < 630)
{print "Normal\n".$line."\n"; $N = 1;$L = 0;$R = 0;$I = 0; normal();}}

if($I != 1 ){if ($x > 490 and $x < 510 and $y > 490 and $y < 510)
{print "Inverted\n".$line."\n"; $I = 1;$L = 0;$R = 0;$N = 0;inverted();}}
goto y1;

sub right{
`metacity --replace`;    
#`lcd-off`;
`xrandr -o right`;
#`lcd-on`;
`compiz --replace`;
}
sub left {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o left`;
#`lcd-on`;
`compiz --replace`;
}
sub normal {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o normal`;
#`lcd-on`;
`compiz --replace`;
}

sub inverted {
`metacity --replace`;    
#`lcd-off`;
`xrandr -o inverted`;
#`lcd-on`;
`compiz --replace`;
}


@tmp = split(',',$line);
$x = $tmp[0];
$y = $tmp[1];
$x =~ s|\D||g;
$y =~ s|\D||g;

if($x < $oldx - 5){$xstat = "left\n"}
if($x > $oldx + 5){$xstat = "right\n"}
if($y < $oldy - 5){$ystat = "down\n"}
if($y > $oldy + 5){$ystat = "up\n"}


if($xstat != 99){
if($x - $oldx > $y - $oldy){print $xstat;}
$xstat = 99;
}


if($ystat != 99){
if($x - $oldx < $y - $oldy){print $ystat;} 
$ystat = 99;
}
$oldx = $x;
$oldy = $y;

#print $x."-".$y."\n";
#for($i =0;$i < 500;$i++){}
sleep 1;
goto y1;

```

---

### Post by hurdevan on 2010-04-03
Nope still gives that same error. And that is:

> 
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_1"


Then my script stops to respond.

---

### Post by mcoleman44 on 2010-04-03
Well then Im not sure. haha. Sorry, I tried.

---

