---
title: "Irfanview wont run on Ubuntu 10.04"
date: 2011-05-17
forum: General Help
---

### Post by victorash on 2011-05-17
Im trying to get Irfanview to run on UBUNTU with WINE.

I have tried opening it with wine and it says it is opening  but nothing happens.

I havent found any programs on Linux that are as easy to use. I ave a lot scaned images and need to have Batch Rename and Batch File conversion options.

Any ideas or Help would be appreciated.

Thanks

---

### Post by jerrrys on 2011-05-17
have you looked [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Irfanview&as_qdr=all&sa=Google+Search&lang=en#806") for irfanview?

as far as bulk tools i use thunar, pyrenamer, and nautilus image converter.  all are in the software center

---

### Post by Tamlynmac on 2011-05-17
Have you tried [XnView]("http://www.xnview.com/en/index.html")? It's very similar to irfanview.

To install it simply download the tar.gz Linux file and open it with the archive manager. Extract the folder directly to your default home directory. It will create a folder called XnView - "number". In that folder you will find a subfolder called bin. Open that folder and select the "xnview" executable file.

At first it will open a very small window from which you select tools/options and set it up (making sure to check launch browser at startup under the browser section). After setup and closing, the next time you open, it will then open into the full blown browser.

Of course you can add this to your menu by edit menu and add new item. Using the executable above.

I think you will find this app very similar to irfanview. I really enjoy the volume of formats it can save a pic/file.

Good Luck.

---

### Post by gsmanners on 2011-05-17
Irfanview does require a special library to work properly.

Install [vcrun6]("http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe") or use [winetricks]("http://wiki.winehq.org/winetricks") vcrun6 to get that working.

See the [appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834") page for more details.

---

