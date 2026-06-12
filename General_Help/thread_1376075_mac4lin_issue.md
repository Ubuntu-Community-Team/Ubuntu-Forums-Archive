---
title: "mac4lin issue"
date: 2010-01-08
forum: General Help
---

### Post by qwerty123321 on 2010-01-08
Does anyone know why my mac4lin (using ubuntu ) look like  this??  	 	 	 	 			[View Image]("http://www.facepunch.com/#") 			[IMG]http://img689.imageshack.us/img689/7913/screenshotey.png[/IMG]
 			
 			 			[http://img689.imageshack.us/img689/7913/screenshotey.png](http://img689.imageshack.us/img689/7913/screenshotey.png)
 			 	
 	 	 	  as oppose to this??  	 	 	 	 			[View Image]("http://www.facepunch.com/#") 			[IMG]http://images.howtoforge.com/images/mac4lin/Mac4Lin%20Documentation_html_m2ad3b0cf.jpg[/IMG]
 			
 			 			[http://images.howtoforge.com/images/mac4lin/Mac4Lin%20Documentation_html_m2ad3b0cf.jpg](http://images.howtoforge.com/images/mac4lin/Mac4Lin%20Documentation_html_m2ad3b0cf.jpg)
 			 	
 	 	 	  notice how My version the bottom left and top left's colors don't match ..

---

### Post by qwerty123321 on 2010-01-08
bump would really appreciate input..

---

### Post by Revolutionary101 on 2010-01-08
The one thing I have noticed is that you have not installed AWN (the dock at the bottom). To install AWN just type this into terminal.

```
sudo apt-get install awn-manager
```

That should at least install the program for the dock. Other than that, I am not sure how to fix the other problems.

---

### Post by qwerty123321 on 2010-01-08
thanks for responding but the dock is the least of my concern :/

I really wanna get this to work :O

for some reason ..version 1.0RC works :O

but version 1 just screws up 

oh well..I guess ill have to stick with 1.0RC

---

### Post by Ginsu543 on 2010-01-09
Give this a try:

1) Right click on the panel and select "Properties"
2) Click on "Background" tab
3) Make sure that "Background image" is selected
4) Make sure that the image is pointed to your_home_folder/.themes/Mac4Lin_GTK_Aqua_v1.0/gtk-2.0/Panel/panel-bg.png

If that doesn't fix the problem, try removing the Menu Bar from the panel and adding it back.

---

