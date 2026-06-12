---
title: "How Lucid supports Calibre and Kindle 3"
date: 2011-12-14
forum: General Help
---

### Post by sallymc on 2011-12-14
As Calibre in the repository doesn't recognise the new Kindle 3, this worked for me :

   1. Install Calibre from the Universe repository using your package manager of choice. 
   2. Press ALT-F2 to bring up a “Run Application” dialogue.
   3. Copy and paste the following line into that dialogue:

      gksudo gedit /usr/lib/calibre/calibre/devices/kindle/driver.py

   4. Enter your password when prompted and you should see “gedit” (text editor) open with the file ready for editing.
   5. Scroll to the bottom of the file.
   6. Copy and paste the following code at the end of the file:

      class KINDLE2(KINDLE):

          name           = 'Kindle 2/3 Device Interface'
          description    = _('Communicate with the Kindle 2/3 eBook reader.')

          FORMATS        = KINDLE.FORMATS + ['pdf']
          PRODUCT_ID = [0x0002,0x0004]
          BCD        = [0x0100]

   7. Save the file and quit “gedit”.
   8. Launch Calibre from the Applications=>Office menu and start managing your eBook collection for your Kindle 3.

---

