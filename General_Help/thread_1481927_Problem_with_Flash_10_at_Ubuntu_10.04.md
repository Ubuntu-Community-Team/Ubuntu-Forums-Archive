---
title: "Problem with Flash 10 at Ubuntu 10.04"
date: 2010-05-13
forum: General Help
---

### Post by gramsyn on 2010-05-13
Hello everyone,

I was using Ubuntu 09.10 and everything worked fine. When I upgrated to the new version, I had no sound using YouTube.

I installed the version Flash 10  and flashplugin-nonfree-extrasound from package manager and the problem was fixed for a few days. Suddenly, I had no sound again. Other sound applications work properly. 

I checked the plugins of Mozilla and discovered that the Shockwave flash version was 9.0 r31! However, the package manager says that the 10 version is installed! 

I tried to upgrade the version of the plugin. It sends me to a link of Adobe where I can download a tar.gz file. I follow the instructions:

[HTML]Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.[/HTML]

When I open the tar.gz file, I only see a file named libflashplayer.so, which is extracted as such. No match with the previous instructions and as a result I cannot follow them to install that file.

Please, do you have any ideas of what should I do???

Thanks in advance

---

### Post by ajack on 2010-05-13
I don't have a solution, but may I suggest you visit the site [http://playerversion.com](http://playerversion.com) to see exactly which version of Flash is actually running?

---

