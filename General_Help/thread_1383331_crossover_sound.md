---
title: "crossover sound"
date: 2010-01-17
forum: General Help
---

### Post by evelin on 2010-01-17
hello, im running a windows application that makes a beep so i can hear it in the speakers, but when i run it crossover i cant hear the beep, what do i need to hear it.

---

### Post by jamesisin on 2010-01-17
What do you mean when you say "run it crossover"?  Are you connecting the machines with a cross-over cable or something different?

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> What do you mean when you say "run it crossover"?  Are you connecting the machines with a cross-over cable or something different?

hello, sorry i miss a "with" 
when i run this .exe application that makes a sound in crossover and in wine i never hear the sound, do i need to add something like a library so it can make the sound?

---

### Post by jamesisin on 2010-01-17
Ah, so when you run this Windows application on a Windows machine it will chime through your speakers in response to some situation.  However, given that same situation you hear no chime while running the application under WINE.

Do any applications under WINE make any sounds?  You may have to point WINE at your audio controller (presumably PulseAudio):

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> Ah, so when you run this Windows application on a Windows machine it will chime through your speakers in response to some situation.  However, given that same situation you hear no chime while running the application under WINE.

Do any applications under WINE make any sounds?  You may have to point WINE at your audio controller (presumably PulseAudio):

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

hello, it didnt work the alsa is already selected, i even tried oss and the others but none is able to make the exe program to make the sound

pos:  and i clicked in the test sound in the wine config and it make a sound, but it cant make sounds from the exe application

---

### Post by jamesisin on 2010-01-17
Hehe.  I think you mean PS.  PS means Post Scriptum (after writing) while PoS means Piece of Sh!t (or sometimes Point of Sale).

Anyway, does the application itself have any audio settings that might need to be configured for use with WINE?

What is the application?

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> Hehe.  I think you mean PS.  PS means Post Scriptum (after writing) while PoS means Piece of **** (or sometimes Point of Sale).

Anyway, does the application itself have any audio settings that might need to be configured for use with WINE?

What is the application?

no, this application is made in autoit the function is called beep() it only makes a sound, and no need to configure anything so it can make it you yust need to click one button to make it

---

### Post by jamesisin on 2010-01-17
The script is probably looking for one of the default Windows sounds:

C:\WINDOWS\Media\[SomeSound.wav]

You need to figure out which one (ding.wav maybe) and make sure it is represented in the WINE hierarchy.

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> The script is probably looking for one of the default Windows sounds:

C:\WINDOWS\Media\[SomeSound.wav]

You need to figure out which one (ding.wav maybe) and make sure it is represented in the WINE hierarchy.

where is the wine hierarchy

---

### Post by jamesisin on 2010-01-17
/home/[username]/.wine/drive_c/windows

You'll have to create the Media directory and then add the relevant wave file (or really any wave file named appropriately).

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> /home/[username]/.wine/drive_c/windows

You'll have to create the Media directory and then add the relevant wave file (or really any wave file named appropriately).

nop it didnt work i copied the entire media directory but stills no sound

---

### Post by jamesisin on 2010-01-17
Can you look into the script and see where it calls out the sound?

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> Can you look into the script and see where it calls out the sound?

```
While 1
	$nMsg = GUIGetMsg()
	Switch $nMsg
		Case $GUI_EVENT_CLOSE
			Exit

		Case $Button1
			
                        function _beep () 
			$OFF = GUICtrlCreateLabel($timer + 1, 80, 72, 24, 17)
		Case $Button2
			Exit
	EndSwitch
WEnd


Func _beep ()    
		Beep(500,500)
		$OFF = GUICtrlCreateLabel($timer + 2, 80, 72, 24, 17)
EndFunc
```


when button 1 is clicked it activated the function beed wich activates the command beeb that makes the sound

---

### Post by jamesisin on 2010-01-17
Do you know which scripting language it is so I can investigate how it works?

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> Do you know which scripting language it is so I can investigate how it works?

its autoit i used the scrit editor


[http://www.autoitscript.com/autoit3/](http://www.autoitscript.com/autoit3/)

---

### Post by jamesisin on 2010-01-17
So are you doing this because you are trying to learn AutoIt or does this script fulfill some useful purpose?

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> So are you doing this because you are trying to learn AutoIt or does this script fulfill some useful purpose?

both

---

### Post by jamesisin on 2010-01-17
It might be in your best interest to instead work with bash which is the shell you run in your terminal window in Ubuntu.  Bash is the most common shell (my Mac runs it and on Windows you can get bash through Cygwin).

(Disclosure: I am studying bash.)

---

### Post by jamesisin on 2010-01-17
I found an AutoIt forum:

[http://www.autoitscript.com/forum/index.php](http://www.autoitscript.com/forum/index.php)

I did a quick search for "wine" and there were plenty of results.  Might be an additional resource.

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> I found an AutoIt forum:

[http://www.autoitscript.com/forum/index.php](http://www.autoitscript.com/forum/index.php)

I did a quick search for "wine" and there were plenty of results.  Might be an additional resource.

i really need this func beep to sound, its for a proyect in the school and it will be best if i present it in ubuntu

---

### Post by jamesisin on 2010-01-17
Ah, I see.  Very important then.

I would post something over at that AutoIt forum.  You may still get some additional help here, but the added exposure certainly won't hurt.

---

### Post by evelin on 2010-01-17
> **jamesisin said:**
> Ah, I see.  Very important then.

I would post something over at that AutoIt forum.  You may still get some additional help here, but the added exposure certainly won't hurt.

thanks for the help, you r a kind man, by the way do u know how to back the entire system so if it fails you can restore it 

i have read that i can backup the entire system with the home folder with commands, or with programs, such as clonezilla, but it doesnt work, so im trying to back it up with commands now but i cant find a good tutorial to explain what commands to use. does someone knows how to do this or where do i find a good tutorial.

---

### Post by jamesisin on 2010-01-18
There is a lot of information around here about clonezilla (though I have not used it myself).  I would search the forums and if you have specific backup questions post those in threads.  Take care to select a good title when you post as this will increase the likelihood that the right person will find your question and be able to answer it.

---

