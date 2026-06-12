---
title: "Background Changer Script"
date: 2009-10-15
forum: General Help
---

### Post by drpain on 2009-10-15
I tried to make it as simple as possible with my limited know how of programming in Linux.
If there are simpler ways go for it.

The script will change your wallpaper every 5 mins, you can change the timeout later.



1. Unzip background_changes.zip to your home directory. 
    The zip file contains the following:
    
    wallpapers (folder with some of my favorite backgrounds)
    
    change_background (script that actually changes the wallpapers)
    
    readme.txt (install / customise info)



2. Make sure your files are in your home folder eg. /home/bounce in my case



3. If you have more wallpapers make sure to copy them to the wallpapers folder where it will be called by the script.



4. Open a Terminal Window,
    
    Type in the following without quotes and enter "chmod 755 change_background"

    To initiate the script type the following in without quotes and enter "./change_background"
    
    
5. It will run and tell you how many images are available, and which image it is setting as the wallpaper. 
    Close the window to stop the script executing.



6. Now right click anywhere on your desktop, and click on "Change Desktop Background". 
    Click on the "Add" button. 
    Navigate to your home folder. 
    Then to wallpapers. 
  
    Look for the image called wallpaper.jpg. 
    Select it and click on "Open". 
    Close the background window.
  


7. Lastly we need to add the script to the crontab so it starts every time we log in.
  
    Open a Terminal Window, then type in "crontab -e" without the quotes and press enter.
  
    Now add the following line "@reboot ~/change_background" without the quotes and save. 
    Refer to the image to see. 
  



Reboot and it will change the background every 5 minutes. 

If you want to change the frequency at which the background changes, open the change_background (Located in your home folder) in gedit. 

Look for the line "sleep_time=300", change this value to change the frequency of the changer. eg. 60 will be every minute, 600 will be every 10 minutes. 



I hope you find this helpfull and easy to use.


Rudi

---

