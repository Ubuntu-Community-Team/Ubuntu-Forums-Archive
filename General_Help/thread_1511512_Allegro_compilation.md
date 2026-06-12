---
title: "Allegro compilation"
date: 2010-06-16
forum: General Help
---

### Post by raac on 2010-06-16
Hi guys I'm stuck trying to test if the Allegro library is being read correctly apparently is not, I need help guys. This is what I've done so far. By the way I'm new with linux

I downloaded allegro 4.2.2
then I looked at the instructions and it said this..   //
//I DID THIS ON THE FILE ALLEGRO4.2.2 (THE ONE THAT I DOWNLOADED)

 From here on everything is a pretty standard Unix-style install process. 
   First you configure it:

      ./configure

   It should automatically build dependencies. Then you build it:

      make

   And finally you install it (as root -- see below for information on what
   to do if you can't be root):

      su -c "make install"

   You may also wish to install the man pages:

      su -c "make install-man"

   And perhaps the info docs as well:

      su -c "make install-info"




-----------------------------------------------------------------------------------------------------
Then I typed this program

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <allegro.h>
int main(void){
        char version[80];
        allegro_init();
        sprintf(version, "Allegro library version = %s", allegro_id);
        allegro_message(version);
        allegro_exit();
        return 0;
}
END_OF_MAIN()

-------------------------------------------------------------------------------------------

Then I tried to compile it like this

gcc -Wall -g first.c -o driver

and i get this message

first.c: In function ‘main’:
first.c:9: warning: format not a string literal and no format arguments
/tmp/ccqbhN1i.o: In function `main':
/home/tony/cs/Practice/GAMING/build/first.c:7: undefined reference to `_install_allegro_version_check'
/home/tony/cs/Practice/GAMING/build/first.c:8: undefined reference to `allegro_id'
/home/tony/cs/Practice/GAMING/build/first.c:9: undefined reference to `allegro_message'
/home/tony/cs/Practice/GAMING/build/first.c:10: undefined reference to `allegro_exit'
collect2: ld returned 1 exit status



THANKS A LOT FOR HELPING ME!!

---

