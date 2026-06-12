---
title: "can't access my ttyUSB0 port"
date: 2010-03-07
forum: General Help
---

### Post by Kaweezonderkap on 2010-03-07
Hi,

I have a question. I'm a new ubuntu (and unix) user and I am doing something wrong ;)

I'm tring to write 3 ascii characters to a comport. I am using a USB=> serial converter. 
The converter is fine (I have tested it with a terminal program).

But when I use the code below, it doesnt work... What am I doing wrong? Do I have to change some other settings so I am allowed to use the port?

greetings

```

#include <termios.h>
#include <stdio.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/signal.h>
#include <sys/types.h>
#include <string.h> 
 
 
void main()
{
 int n, mainfd=0;                                            /* File descriptor */
 char chout;
 struct termios options;
   
 mainfd = open_port();

 fcntl(mainfd, F_SETFL, FNDELAY);                  /* Configure port reading */
                                     /* Get the current options for the port */
 tcgetattr(mainfd, &options);
 cfsetispeed(&options, B19200);                 /* Set the baud rates to 9600 */
 cfsetospeed(&options, B19200);
    
                                   /* Enable the receiver and set local mode */
 options.c_cflag |= (CLOCAL | CREAD);
 options.c_cflag &= ~PARENB; /* Mask the character size to 8 bits, no parity */
 options.c_cflag &= ~CSTOPB;
 options.c_cflag &= ~CSIZE;
 options.c_cflag |=  CS8;                              /* Select 8 data bits */
 options.c_cflag &= ~CRTSCTS;               /* Disable hardware flow control */  

                                 /* Enable data to be processed as raw input */
 options.c_lflag &= ~(ICANON | ECHO | ISIG);
       
                                        /* Set the new options for the port */
 tcsetattr(mainfd, TCSANOW, &options);
                         
 while(1)
 {
   n = write(mainfd, 0x230,1);
   n = write(mainfd, 0x120,1);
   n = write(mainfd, 0x120,1);

 }
                                                    /* Close the serial port */
  close(mainfd);
 }

 
 int open_port(void)
 {
   int fd;                                   /* File descriptor for the port */

   fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);

   if (fd == -1)
   {                                              /* Could not open the port */
     fprintf(stderr, "open_port: Unable to open /dev/ttyS1 - \n");
   }

   return (fd);
 }


```

---

