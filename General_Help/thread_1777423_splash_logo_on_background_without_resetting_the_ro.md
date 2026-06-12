---
title: "splash logo on background without resetting the root"
date: 2011-06-07
forum: General Help
---

### Post by rbhkamal on 2011-06-07
I'm setting the root window background to a gradient with the following command:
```

DISPLAY=:0 fbsetroot -gradient Elliptic -from blue -to black

```

What I would like to do next is to display a small logo in the center of the background without resetting the root window background color. Right now I tried the following two commands and they both reset the root window to a solid color... I would like to keep the gradient color.
```

vmsetbg -e logo.png # resets the root window
fbsetbg -c logo.png # also does the same thing

```

I cannot use just a single image because the same image has to look good on all screen sizes from netbooks to 52" TVs

Thanks,
RK

---

### Post by rbhkamal on 2011-06-09
For all who are looking for a similar functionality, I have modifed fbsetroot to do just want I need.

I only changed it for the gradiant background since the other types can be easily done wirh Esetroot.

Attached are the modified code, download fluxbox src V1.3.* and move the attached source files to util. After you've compiled the code, just run it like this:
```

DISPLAY=:0 fbsetroot -gradient Elliptic -from blue -to white -splash /tmp/logo.png

```

Note, this will not scale the splash image down if the screen resolution is smaller than the splash image. If you want to do it, look at how Esetroot does it.

---

