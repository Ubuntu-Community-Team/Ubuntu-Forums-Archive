---
title: "is there any way to batch process files in gimp?"
date: 2011-12-11
forum: General Help
---

### Post by blackdalek on 2011-12-11
Is there any way to streamline this process?
This is what I want to do -

1. open a multi page PDF in gimp, at 100dpi, as separate images.

2. change image's mode to indexed 16 colours, dithered.

3. save image as xx.png (where xx is a number incremented by 1)

4, close the image.

5. go back to step 2 for next image, continuing until all pages in PDF are saved.


So the end result for a 5 page PDF would be:

01.PNG
02.PNG
03.PNG
04.PNG
05.PNG

Any suggestions? Because I've been doing this manually and I am getting tired of it.

Thanks for your help.

---

### Post by blackdalek on 2011-12-19
So the answer is........





                         no.





Thread solved???

---

### Post by spcwingo on 2011-12-19
You can try the GIMP plugin registry, although I have no idea if it will do exactly what you want.  On the other hand you can do batch editing by installing that package.  To install, use this command in a terminal:

```
sudo apt-get install -y gimp-plugin-registry
```

---

