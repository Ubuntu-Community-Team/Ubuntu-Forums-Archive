---
title: "Problem using font weights/styles"
date: 2010-10-12
forum: General Help
---

### Post by eiolv on 2010-10-12
I'm having a problem with a font that comes in several weights/styles. While running Microsoft Word or OpenOffice Writer on Windows, each weight/style comes up as a separate font. The weights/styles are roman, bold, italic, medium, bold italic, medium italic and small cap. 

Running on OpenOffice Writer the font appears as one font in the drop down menu, and works only with medium and medium italic. If i tries to make it bold, it only makes the medium bolder, and does not use the bold weight. 

After doing some research, I found that OpenOffice does not work with otf-fonts, and my font being of open type, I thought that was the problem. I then converted the font with all its weights/styles using the procedure described [here]("http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html"). 

But it did not help. I have deleted the otf-version of the font, and run the sudo fc-cache -f -v command, but I still am only able to use the medium and medium italic weights. 

Any suggestions?

---

