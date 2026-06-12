---
title: "Screen Resolutions"
date: 2004-10-22
forum: General Help
---

### Post by wtd on 2004-10-22
I realize this is probably FAQ material, but searching the FAQ foum didn't turn up anything (though I don't claim to be a searching expert).

When I go to System Configuration -&gt; Screen Resolution, the only two options I'm given are 800x600 and 640x480.  I had previously run FC2 at 1024x768, so I know the system can handle it.  /etc/X11/XFConfig-4 seems to indicate that XFree feels my system can handle it as well.  

How do I get the Screen Resolution app to agree?

---

### Post by umarmung on 2004-10-22
I'm not sure what exactly 'XFConfig-4 seems to indicate...' mean, but check your config file for some lines like these:
```

Section &quot;Screen&quot;
        Identifier      &quot;Default Screen&quot;
        Device          &quot;NVIDIA Corporation NV34 &#91;GeForce FX 5200&#93;&quot;
        Monitor         &quot;Belinea&quot;
        DefaultDepth    24
        SubSection &quot;Display&quot;
                Depth           1
                Modes           &quot;1280x1024&quot; &quot;1152x864&quot; &quot;1024x768&quot; &quot;800x600&quot; &quot;640x480&quot;
        EndSubSection
        SubSection &quot;Display&quot;
                Depth           4
                Modes           &quot;1280x1024&quot; &quot;1152x864&quot; &quot;1024x768&quot; &quot;800x600&quot; &quot;640x480&quot;
        EndSubSection
&#91;...&#93;

```
Your XF86Config-4 should list 1024x768 in all of the lines.

---

### Post by wtd on 2004-10-22
My apologies.  That is the file I was referring to.  I was just posting really late at night.  :)

As for the file, that's what it looks like, though "1024x768" is the largest resolution listed.

---

### Post by flygmaskin on 2004-10-23
Make sure that your "Monitor" section has the correct HorizSync and VertRefresh values.

If that doesn't help, you could try removing "800x600" and "640x480" from your XF86Config-4. Leaving only "1024x768".

---

