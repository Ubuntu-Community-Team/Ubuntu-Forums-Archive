---
title: "Typing ascii codes especially for accents"
date: 2009-11-13
forum: General Help
---

### Post by DiegoDeEscocia on 2009-11-13
Hi All,

I used to use ubuntu ages ago with my old computer but a few packages I needed made me take a brief holliday. Love of our fine OS has drawn me back.


I've encountered a problem with the new version Ubuntu 9.10 - something that would never have been a problem before but now is massive:

I've been learning spanish. I write to a lot of Spanish friends frequently and I need to be able to type accents. I learned to be able to do it very quickly and efficiently in Windows using the ascii codes. As a touch typer I was loath to try switching to a spanish keyboard and have got to the point that I get on quite well and can even type quite quickly with a normal UK keyboard....

I'm using a Dell Latitude D420 and so to render accents I need

1. numlock on (it is)
2. To hold down both Fn and Alt
3. To enter the specific codes....


This plain and simply isn't working now......Anyone know how I fix it? I'd rather enable this than try learning a new system if possible. All help greatly appreciated!


I can't emphasise how important this is - for example:


tengo 21 anos - with the correct accent on the n this means 'I'm 21 years old'

Without this it means 'I have two anuses'!

Thanks all!

Iain (o cuando hable espanol Diego - forgive the use of a normal n in espanol - I can't write the correct symbol!)

---

### Post by delcypher on 2009-11-13
Looks at```
man iso_8859-1
```

Scroll down there is a list of Hex codes

When you want to use one press CTRL+SHIFT+U and type the hex code and enter.
I'm pretty sure the u actually means unicode but I couldn't find a manual containing a list. But I tried a few hex codes from iso_8859-1 and that worked fine for me.

There you go!

In fact I've discovered you can goto "Applications > Accessories > Character Map" and that works fine too :D

---

### Post by audiomick on 2009-11-13
Hallo.
try this:
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

I haven't tried it, I just went and found it;)

---

### Post by DiegoDeEscocia on 2009-11-14
Thanks for your help folks, I took a look!

Editing the config files myself to create a custom keyboard layout.... sounds like a headache of a project.....

As for insert symbols - well yes it works except that I need them so regularly that it really slows my typing down.

On the manual entry you directed me to the HEX codes are all right next to the ASCII codes I've already memorised.

Guess the question boils down to this:

is there any way to set it up that I can use typing the decimal ascii codes to enter symbols? eg ALT+ 0225 for an 'a' with an acute accent on it? If worst comes to the worst I'll have to learn how to use a composer or HEX codes or even *gulps* try and edit the keyboard layout....

but I'd really be over the moon if there were just some way to switch on ascii code entry? Mighty ubuntu must be able to do this somehow???

Also anyone know where the gnome session manager went? I'm having problems trying to start xsessions of other window managers simultaneously on other screens manually.

---

### Post by DiegoDeEscocia on 2009-11-15
Thanks to those above for their help!

Right in case anyone else hits the problem I hit, and for the sake of posterity:


I still don't know how to enter decimal ASCII codes. If anyone discovers how to do this please do drop me a PM :-)

However there is a way round it, and it's actually superior to ASCII codes....Not that I wouldn't like to have both options....Still fewer keystrokes and a logical sequence so there's less memorisation involved. You should actually be able to guess what you need to enter for any given accent.

In Gome:

System > Preferences > Keyboard

Goto the 'Layout' Tab

Select 'Layout Options'

Under 'Compose Key Position'

Chose 'Right Alt' (that's the 'Alt Gr' button).

Now close the layout options window and click the 'Apply System Wide' option.

You're now ready to go.

For example place the cursor somewhere....now hold down AltGR + ; (then release the two) next type 'e'.

And BAMN! -  é (and yes I used it to write that character).

That AltGr+apostrophy works for all Acute accents...so you should be able to guess:

í á é ó ú ý 

If you want grave accents its ALTGr+# (then release the two)  then the letter of your choice:

Eg AltGr + # then e &#8594; è

And you can guess:

à è ì ò ù &#7923; .............

the button in between those two gives you ^ 

so AltGr + '  &#8594; ^

as in:

ê â î ô û &#375;

y antes de acabar esta discusión voy a darte la letra más importante si tiene ganas de escribir en español.... y por supuesto eso es...................

[SIZE=7]               ñ[/SIZE] 


You'll need to combine AltGr + ~ then the letter (n of course)

So you need to type 'AltGr + SHIFT + #'  **then release the keys*** then 'n'

Remember Shift + # = ~

So AltGr + Shift + #  = AltGr + ~ ............ Which makes it easier to remember!

Oh and AltGr + !   &#8594; ¡ 

But for ' ¿ ' you will have to type the ? twice

AltGr + ??  &#8594; ¿

Hope that helped you all!

Check out:

[http://en.wikipedia.org/wiki/Compose_key](http://en.wikipedia.org/wiki/Compose_key)

and 

[http://hermit.org/Linux/ComposeKeys.html](http://hermit.org/Linux/ComposeKeys.html)

¡Buena suerte a todos!

---

