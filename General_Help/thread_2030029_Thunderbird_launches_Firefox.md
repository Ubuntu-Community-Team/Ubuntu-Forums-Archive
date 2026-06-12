---
title: "Thunderbird launches Firefox"
date: 2012-07-20
forum: General Help
---

### Post by waffen on 2012-07-20
Hello,
In Ubuntu 12.04 I can see this behaviour:in my thunderbird screen when I click in any link inside of email, that action show me the firefox immediately loading the page... that avoid me continue reading the email or click in others links. so I need do ctrol + tab and comeback to TB to continue my reading....
Is there a way to avoid it? so firefox (already open) can load the page behind the scene?

---

### Post by TheFu on 2012-07-20
If I understand correctly, you'd like firefox to open tabs in the background and not be pulled to the top with focus from an external program URL request.

I don't know the answer, but found this [http://lifehacker.com/263940/force-links-to-open-in-the-background](http://lifehacker.com/263940/force-links-to-open-in-the-background) which might help.

When I did a  **man firefox** there wasn't a clear command line option to prevent raising the window. That would probably be dependent on your window manager and focus settings.  Openbox is what LXDE uses, this page [https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox) explains some of the options.

I found an openbox guide that showed configuration settings like these:
```

<application name="xfce4-terminal">

[LIST]   <desktop>3</desktop>
  <layer>below</layer>
  <decor>no</decor>
  <maximized>yes</maximized>
</application>
[/LIST]

```
The **layer** might be important, though the *maximized=yes *is just scary.

It appears to be that your window manager and DE will determine how this behaves.

Another idea is to place the Firefox program onto a different virtual desktop from thunderbird. When I client a link in thunderbird, what firefox does isn't seen (FF opens the link inside a new tab) so I'm not distracted.  I tested it and it does work.

---

### Post by waffen on 2012-07-20
> **TheFu said:**
> ....
I don't know the answer, but found this [http://lifehacker.com/263940/force-links-to-open-in-the-background](http://lifehacker.com/263940/force-links-to-open-in-the-background) which might help.


Yes!! thats! thanks!

---

