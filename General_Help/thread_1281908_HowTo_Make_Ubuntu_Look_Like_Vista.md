---
title: "HowTo: Make Ubuntu Look Like Vista"
date: 2009-10-03
forum: General Help
---

### Post by Arceux on 2009-10-03
**Introduction**
 

 -I've been reading around and haven't been able to find a simple all-in-one tutorial on hot to make **[IMG]http://ubuntuforums.org/home/thomas/desktop/Tutorial/Pictures/Emerald.png[/IMG]**your desktop look like Windows Vista. So I decided to make and account on the forums just to let everybody know how to do it.
 
 **Programs Required ** 
 
 -Before I start blabbering on about how to install this package properly you're going to need to install &#8220;Emerald&#8221; and &#8220;GnoMenu&#8221;. There is one other optional program called &#8220;Screenlets&#8221;.
 
 -To install &#8220;Emerald&#8221;, open your &#8220;Synaptic Package Manager&#8221; and search emerald. Check the box and hit apply (you will be prompted to enter your password). Once it's installed close the &#8220;Synaptic Package Manager&#8221;
 

 -To install GnoMenu open the folder in the &#8220;Vista&#8221; folder and open the file &#8220;gnomenu_1.9.6-6_all.deb&#8221;. click &#8220;Install Package&#8221; (you will be prompted to enter your password). Once the package is installed, you're ready to begin the installation process.
 

 **Installation**
 

 -To begin the process you'll need to delete the panel at the top of your screen (this can be done by right clicking on the panel and selecting delete). Now that your upper panel is gone you need to delete everything that is on your lower panel. You should now be left with a bare panel on the bottom of your screen. Right click on that panel and click &#8220;Properties&#8221; and change the &#8220;Size&#8221; value to 32.
 

 -Return to the desktop if not already there and right click in open space. Click on the option &#8220;Change Desktop Background&#8221;. Up towards the top click on the &#8220;Themes&#8221; tab and press the &#8220;Install&#8221; button towards the bottom right of the window. Under the &#8220;Themes&#8221; folder open the &#8220;aero-clone.tar.gz&#8221; file. Once the theme is installed you will be asked if you would like to apply it now, select yes and close the appearance window.
 

 -To get the Windows Start Button you'll need to right click on the open panel and select the option &#8220;Add to Panel&#8221;. Scroll down until you find the &#8220;GnoMenu&#8221; application. Click add and move the applet to the left-most side of the panel. Once you have it where you would like it right-click and lock it in place. Next you want to change the orange foot icon into a nice Windows icon, to do this right click on the orange foot and select the &#8220;Preferences&#8221; option. Under each tab change the little drop down to &#8220;Vista&#8221;. Do this for every tab except &#8220;Program Widgets&#8221;.
 

 -Right now your panel probably looks a little bare so now I'm going to tell you how to add more applets onto it. To start right-click on the panel and select &#8220;Add to Panel&#8221;. Click &#8220;Application Launcher&#8221;, you should come up with a list of categories. Click the little arrow next to &#8220;Internet&#8221; and highlight firefox, then hit add (if you want to change the icon I have included a suggestion in the package). Move the firefox icon to the right of your GnoMenu applet and lock it in place when you are satisfied. Now do the same thing, but instead of making a launcher you can just scroll down until you find the &#8220;Window List&#8221; applet. Add that and move it to the right of your firefox launcher and lock it in place. I suggest you also add the clock applet (looks best with the just time, no date or seconds).
 

 -This is optional, but if you want everything to look more like windows you need to apply the Segoe UI font I've included in the package. To do this copy the contents of the &#8220;Window Font&#8221; folder and place them inside the &#8220;.fonts&#8221; folder under your home folder (make sure you have view hidden files checked). If the isn't a .fonts folder you need to create one. Now open up your appearance menu by clicking on your GnoMenu and selecting &#8220;Control Center&#8221;. Under the tab &#8220;Fonts&#8221;  change &#8220;Window title font&#8221; to Segoe UI.
 

 

 -Getting those sleek glass windows is probably going to take the most work so let's start by opening up the &#8220;Emerald Theme Manager&#8221; the same way you opened the &#8220;Appearance&#8221; menu. Once you have it up select the import button and open the &#8220;Vista.emerald&#8221; file inside the &#8220;Emerald Theme&#8221; folder. Once it has been imported click on it and it should become highlighted, then click the &#8220;Emerald Settings&#8221; button up top. Un-check every check box except the one at the top. Then change the &#8220;Compiz Decoration Blur Type&#8221; to &#8220;All Decoration&#8221; and hit the quit button. Return to the control center and open &#8220;Startup Applications&#8221;. Click add and input the following information. Name: Emerald, Command: emerald &#8211;replace, Comment: Vista. Then click &#8220;Save&#8221; and close all windows. You now need to reboot your system.
 

 -Once you are logged in again go back to your control center and back to appearance. We're now going to change the icon set to the defaults for Vista. Under &#8220;Themes&#8221; click install and find &#8220;Icon Theme&#8221; folder. Select the file &#8220;nuoveXT.2.2.tar.bz2&#8221; and install it. When you are prompted to apply changes select yes. Keep the appearance window open.
 

 -In the &#8220;Appearance Menu&#8221; select install again and find the file under &#8220;Cursor Theme&#8221;, it should be called &#8220;aero-drop.tar.gz&#8221;. Once it is installed click apply when prompted and click on the &#8220;Backgrounds&#8221; tab. Click add and select on of the two default wallpapers I've provided (under &#8220;Vista Wallpaper&#8221;)
 

 -The last thing you could do if you wanted to is add Screenlets. To do this you need the &#8220;Screenlets&#8221; application first though. In the package I've provided a system monitor screenlet that looks like the Window's one.
 

 **Support**
 

 -If support is needed, private message me or leave a post in the thread.


**Downloads**


-Download the latest package here ([http://www.mediafire.com/?tj0mnxz1dfz](http://www.mediafire.com/?tj0mnxz1dfz))

---

