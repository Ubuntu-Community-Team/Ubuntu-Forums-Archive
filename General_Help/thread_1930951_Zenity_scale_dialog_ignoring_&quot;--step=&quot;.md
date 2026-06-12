---
title: "Zenity scale dialog ignoring &quot;--step=&quot;"
date: 2012-02-24
forum: General Help
---

### Post by theBruno on 2012-02-24
Hi all, I hope this question is in the correct forum category and I found no other references to this in the forums here or any bug info...

I am attempting (in both Ubuntu 10.04 & 11.04) to use a zenity scale dialog to allow the user to select and return a multiple of 5 quantity from 5 to 40, with a default value of 10 and a step value of 5 as follows:

```
zenity --scale --title="Quantity" --text="How many copies?" --min-value=5 --max-value=40 --value=10 --step=5
```

Everything works as expected except it seems to ignore the 'step' value. I am able to select any quantity from 5 to 40 and it selects and returns the value without any constraint.

I appreciate any help you can provide.

~theBruno :)

---

### Post by Paddy Landau on 2012-02-25
You need to specify a starting value. Try this command.
```
zenity --scale --title='Quantity' --text='How many copies?' --value=5 --min-value=5 --max-value=40 --step=5
```BTW, I would recommend you have a look at yad as a more functional fork of zenity.

[LIST]
[*][http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html](http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html)
[*][http://code.google.com/p/yad/](http://code.google.com/p/yad/)
[/LIST]
  ```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
```

---

### Post by theBruno on 2012-02-27
Paddy -
Thanks for attempting to help and I have installed yad, but it also seems to ignore the step value.

To clarify that I am thinking correctly:
'--step=x' should constrain the selection to a multiple of x, correct?

Thanks again,
theBruno

---

### Post by Paddy Landau on 2012-02-27
Well, now I am horribly confused. When I tested the command I gave you  in the previous post, it worked. Now I try the same command again, and  it doesn't.

I also have the same problem with yad.

I am utterly flummoxed.

> **theBruno said:**
> '--step=x' should constrain the selection to a multiple of x, correct?
Yes, that is correct. With your command, you should be able to choose only 5, 10, 15, 20, 25, 30, 35 and 40.

What I have found is that when you adjust it with the keyboard (left and right arrow keys), it obeys the scale, but the mouse does not.

I would raise this as a bug report for both Zenity and Yad.

In the meantime, your script will have to check the values.

---

### Post by theBruno on 2012-02-27
Yes, I can confirm that keyboard arrow keys are in fact constrained to the step value, but the mouse is not. :confused:

Thanks again for your replies!

~theBruno

---

