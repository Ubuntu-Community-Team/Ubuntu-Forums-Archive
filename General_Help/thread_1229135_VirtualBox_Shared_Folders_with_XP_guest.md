---
title: "VirtualBox Shared Folders with XP guest"
date: 2009-08-01
forum: General Help
---

### Post by VipX1 on 2009-08-01
[LEFT]                                         
[LIST=1]
[*]On     Ubuntu desktop go to **System**,     **Administration**,     **Software Sources**. In     the **Software Sources**     GUI go to **Third Party Software**.     Click the **+Add**     button.     To find the Repository you need for your version of Ubuntu     go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)     and copy and paste the **deb**     line that applies to you. I am running 9.04 Jaunty so I copied  **deb *** jaunty non-free **and pasted into the **+Add**     box. Next you need the key for that repository, click the '[here]("http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc")' link on the web page. The key will open in     Firefox and you will need to save the key web page to your desktop     by clicking **File** and **Save As** and then **Save**     again. Now open a terminal window in Ubuntu. **Applications**,     **Accessories** and **Terminal**. Type or copy and paste the     following:```
cd Desktop
```Press Return```
sudo apt-key add sun_vbox.asc
```Press Return. You will see the output **OK** in the Terminal window. You can Delete the key from your Desktop if you wish. Close the **Software Sources** GUI and click **Reload** when asked.
[*]On the [Running] GUI click **Devices** and **Install Guest additions**. Allow it to download the **.iso** file. Select **Mount** when asked, **Next**,** Agree**, **Next**, **Continue Anyway**,** Continue Anyway** and then reboot the guest. When the guest restarts the mouse should intergrate between the host and the guest freely and without you having to press the **Ctrl** key.
[*]**Shared Folders** is also in the Devices menu on the guest [Running] GUI. Open the **Shared Folders** GUI and click **add Shared Folders button** in the top right corner. At the end of the folder path box click the drop-down menu and click** Others**. Locate the **Public** directory in your **home** directory. click** Open** when the **Public** folder is highlighted. Now tick the** Make Permanent **box and click **OK**.
[*]In the guest XP open **My Computer** and the **Tools** menu. Click the firs option **Map Network Drive**. Click the **Browser** button.Click the** +plus** beside **VirtualBox Shared Folders**. Your shared **Public** folder will appear. Click the **Public** folder and then** OK**. *Wait for a second..*. Now, click the **VirtualBox Shared Folders** again. Now click the **Public** folder again and **OK** again. This time the window closes and you have something similar to* VBOXSVR\Public* in the folder box.Click **Finish.** The drive window will open on the XP desktop.
[/LIST]
                                  [FONT=FreeSans, sans-serif]I noticed from other posts when I was looking for a solution to the shared folders issue on VirtualBox-OSE
that it was a recuring problem for everybody who used VirtualBox-OSE. It is a small bug that has caused 
me alot of trouble. The solution was simple enough. It's the order in which you click on the shared folders.
Sorry if I over explain things for some of you but it's so as that everyone can understand.
[/FONT]                                   [FONT=FreeSans, sans-serif]
[/FONT]                                      [/LEFT]

---

### Post by ZhuaSD on 2009-08-05
Thanks for this post, it is a big help.  Quite timely&#65281;!  :P

I had added in my desktop before, as I read somewhere that this will provide complete integration.  So I followed your instructions both for the public folder and for the desktop folder.

...and as I wanted access to my storage partition, I simply added another shared folder through the same process, for the whole partition.

Looks good so far, thanks for your help!!

---

