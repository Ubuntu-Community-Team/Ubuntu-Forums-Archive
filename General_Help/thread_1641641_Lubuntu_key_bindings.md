---
title: "Lubuntu key bindings"
date: 2010-12-09
forum: General Help
---

### Post by davidstoll on 2010-12-09
I have a remote that is NOT Lirc.  It is detected as a keyboard.  It has buttons that can be customized, but I can't tell what they are currently assigned to.  It seems two of them do something and the other two don't have anything assigned to them...but I'm not 100% sure.

I would like to....

1) be able to hit a button on my remote (i.e. keyboard) and have a program echo back to me what I just pressed (i.e. Alt+T)

2) I would like to assign a shell script to a button (i.e. keyboard combination).  Preferably with a GUI, but text is ok too.

I tried xbindkeys, but I'm not sure how to use it because the config file says not to edit it and that it will be refreshed on startup (or something to that effect).

My preference would be a GUI where it would wait for (record) a keypress and then ask me what I want (script) to assign to it.

Any other suggestions?

Thanks!

---

### Post by SteveDee on 2010-12-09
> **davidstoll said:**
> 
I would like to....

1) be able to hit a button on my remote (i.e. keyboard) and have a program echo back to me what I just pressed (i.e. Alt+T)



You could write a very simple program to do this. For example using Gambas, just create a new project (which automatically creates a form/window) and add this code:-
```

PUBLIC SUB Form_KeyPress()
DIM varKey AS Variant
   
  varKey = Key.Code
  
  ME.Caption = (varKey)
  
END

```
...as each key is pressed, the key code is written into the window bar. You could then compare these codes with a real (qwerty) keyboard to work out which key is pressed.

Or, if you want a direct indication of the key pressed:-
```

PUBLIC SUB Form_KeyPress()
DIM strKey AS String
DIM varKey AS Variant
  
  IF Key.Control THEN 
    strKey = "<ctrl>"
  ELSE IF Key.Shift THEN
    strKey = "<shift>"
  ELSE IF Key.Meta THEN 
    strKey = "<meta>"
  ELSE IF Key.Alt
    strKey = "<alt>"
  ELSE 
    SELECT CASE Key.Code
    	CASE Key.Space
    	strKey = "<space>"
    	CASE Key.F1
    	strKey = "<F1>"
	CASE...
        ...{add all Gambas key constants}
	
    	CASE ELSE 
    	strKey = Key.Text
    END SELECT 
    
  ENDIF 
  varKey = Key.Code
  
  ME.Caption = (strKey & ", " & varKey)
  
END

```

Key bindings in Lubuntu are defined in: /home/{user}/.config/openbox/lxde-rc.xml

---

### Post by davidstoll on 2010-12-09
> **SteveDee said:**
> You could write a very simple program to do this. For example using Gambas, just create a new project (which automatically creates a form/window) and add this code:-
```

PUBLIC SUB Form_KeyPress()
DIM varKey AS Variant
   
  varKey = Key.Code
  
  ME.Caption = (varKey)
  
END

```
...as each key is pressed, the key code is written into the window bar. You could then compare these codes with a real (qwerty) keyboard to work out which key is pressed.

Or, if you want a direct indication of the key pressed:-
```

PUBLIC SUB Form_KeyPress()
DIM strKey AS String
DIM varKey AS Variant
  
  IF Key.Control THEN 
    strKey = "<ctrl>"
  ELSE IF Key.Shift THEN
    strKey = "<shift>"
  ELSE IF Key.Meta THEN 
    strKey = "<meta>"
  ELSE IF Key.Alt
    strKey = "<alt>"
  ELSE 
    SELECT CASE Key.Code
    	CASE Key.Space
    	strKey = "<space>"
    	CASE Key.F1
    	strKey = "<F1>"
	CASE...
        ...{add all Gambas key constants}
	
    	CASE ELSE 
    	strKey = Key.Text
    END SELECT 
    
  ENDIF 
  varKey = Key.Code
  
  ME.Caption = (strKey & ", " & varKey)
  
END

```

Key bindings in Lubuntu are defined in: /home/{user}/.config/openbox/lxde-rc.xml

Sounds interesting, but I went to apt-get it and it said it wanted to download 225MB?!?

The requirements for this particular machine need to be pretty light.  Is there a lighter wight program or way to do it?

---

### Post by SteveDee on 2010-12-10
> **davidstoll said:**
> ...Is there a lighter wight program or way to do it?

I've created an installable (deb) file of the key press program, but I can't think of a way to get it to you. I can't attach a deb here, and even changing the file extension does not "fool" the uploader into accepting the file...any ideas?

---

### Post by davidstoll on 2010-12-12
> **SteveDee said:**
> I've created an installable (deb) file of the key press program, but I can't think of a way to get it to you. I can't attach a deb here, and even changing the file extension does not "fool" the uploader into accepting the file...any ideas?

Can you post a link here?  If it isn't hosted anywhere, you can drop it at any of a number of web sites that have file sharing dropping services.

---

### Post by SteveDee on 2010-12-13
> **davidstoll said:**
> Can you post a link here...

...attached

---

### Post by davidstoll on 2010-12-13
> **SteveDee said:**
> ...attached

That is a png file...?  Not sure what to do with that.

---

### Post by cavalier911 on 2010-12-13
The packages are located at the url illustrated in the png file.

---

### Post by davidstoll on 2010-12-13
> **cavalier911 said:**
> The packages are located at the url illustrated in the png file.

All I can see is...

[domain blocked]

and there is a .plus or something too, but I can't read it.

In any case, the link isn't working.

---

### Post by davidstoll on 2010-12-13
Is this the same thing?

[http://gambas.sourceforge.net](http://gambas.sourceforge.net)

I hesitate to use something that was PM'ed to me.

---

### Post by SteveDee on 2010-12-14
> **davidstoll said:**
> Is this the same thing?

[http://gambas.sourceforge.net](http://gambas.sourceforge.net)

I hesitate to use something that was PM'ed to me.

The keypress deb is just the simple code in post #2, packaged so that it will run as a program without installing the Gambas development environment.

If you are worried about malicious content, you could create a bootable Ubuntu memory stick and only run the program from there.

Or better still, you could install Gambas via Synaptic, create your own app based on post #2, check your keyboard codes, then remove Gambas.

---

