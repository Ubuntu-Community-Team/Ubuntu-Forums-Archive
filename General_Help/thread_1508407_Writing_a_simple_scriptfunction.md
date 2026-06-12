---
title: "Writing a simple script/function"
date: 2010-06-12
forum: General Help
---

### Post by ksaul on 2010-06-12
I use this command very often inorder to burn xbox games and it would be alot easier if i could just make a commannd line function where i pass it the location of the .dvd/.iso file.

> 
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=<LOCATION OF THE .ISO FILE>

was thinking it could work something like this

> 
cd /home/user/desktop/FOLDER LOCATION OF ISO
burnGame <NAME OF .ISO>.iso


any help, or if someone wants todo it for me? ):P

---

### Post by stinkeye on 2010-06-12
What about using a bash alias for```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=
```


Add something like
```
gameburn='growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd='
```
to your **.bash_aliases** file
And then in the terminal just type gameburn followed by the location.

---

### Post by ksaul on 2010-06-13
> **stinkeye said:**
> What about using a bash alias for```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=
```


Add something like
```
gameburn='growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd='
```
to your **.bash_aliases** file
And then in the terminal just type gameburn followed by the location.

im new to ubuntu/gnome how do i do this? what you replied with is exactly what im looking for!

---

### Post by ksaul on 2010-06-13
Did some googling and went with this method:

> 
Use your favorite editing program and edit ~/.bashrc

[quote]
function burnGame ()
{
  growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=$1
}

Then save the file and quit. Then go to the command line and do "source ~/.bashrc" will make the changes live.
[/quote]

---

