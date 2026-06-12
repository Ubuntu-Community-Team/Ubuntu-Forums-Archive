---
title: "HowTO: xmms hotkeys"
date: 2006-01-21
forum: General Help
---

### Post by Nacker on 2006-01-21
Greetings everybody,
I think, this way to make xmms hokeys work might be interesting for somebody, so here it goes. You'll have to complete several configuration steps to get that working:
1. Download and install xmmsctrl plugin from  [here]("http://user.it.uu.se/~adavid/utils/"). Just follow the installation instructions found within the package. To test the plugin just issue couple of simple commands in the console: "xmmsctrl launch", "xmmsctrl quit" and in case everything appears to be working, continue with the step 2.
2.Download the script I wrote from the attachement below, rename it to something more apropriate for the script file :D (i.e. xmmshotkeys.sh) and chmod it to executable.
3. Now, try to run this script by passing some of the acceptable parameters to it (i.e. "./xmmsctrl up", "./xmmsctrl down" etc...). The list of the acceptable parameters:
[LIST]
[*]up - increases volume by 5%. Maximum value is set to 80% (Can be changed in the script)
[*]down - decreases volume by 5%
[*]v00 - sets the volume to 0%
[*]v25 - sets the volume to 20%
[*]v50 - sets the volume to 40%
[*]v75 - sets the volume to 60%
[*]v100 - sets the volume to 80%
[*]prev - jumps to the previous song
[*]next - jumps to the next song
[*]fw - skips 10 seconds forward
[*]bw - skips 10 seconds backward
[*]playpause - toggles play/pause modes
[*]play - starts the playback from the beginning of the song
[*]stop - stops the playback of the song
[*]runquit - to launch or quit xmms player
[/LIST]
4. Next step is to map xmmshotkeys.sh script to actual hotkeys. Open Configuration editor. Go to the apps -> metacity -> keybinding_commands section. Then modify one of the command_X keys (i.e. command_1) so it could run xmmshotkeys.sh script with one of the parameters (i.e. "/home/user/xmmshotkeys.sh up"). Now, go to the apps -> metacity -> global_keybindings section and assign key combination to one of the run_command_X keys (i.e. the modification of the run_command_1 key to "<Conrtol><Alt>Q" will allow the volume to be increased by 5% each time the key combination Ctrl+Alt+Q is pressed). Now, assign the hotkeys for every other parameter you need.
5. Fell free to modify the script as you like so it could fit your needs.

---

### Post by johannes on 2006-01-31
Thanks for this guide. I had some trouble making xmmsctrl from source, but I found a [Debian package]("http://www.mepislovers-wiki.org/mepislovers/downloads/programs/superkaramba/xmmsctrl-1.8_1.8-1_i386.deb") that works fine.

---

### Post by bluebyt on 2006-02-19
I don't ge this part  "and chmod it to executable", what should I do?

---

