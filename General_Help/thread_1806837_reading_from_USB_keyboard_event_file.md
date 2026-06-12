---
title: "reading from USB keyboard event file"
date: 2011-07-18
forum: General Help
---

### Post by mathio on 2011-07-18
[SOLVED]
Hi all,
I have a problem with reading USB keyboard event file. I can read this file and also decode the characters but the problem is that some characters from this file are read multiple times. Like I type on my keyboard the word water and my application reads from keyboard event file waateer, wwater, or whatever. I've been looking for this all over the Internet and I didn't find anything useable to solve this problem yet. Could anyone help me with this?
Or could anyone explain me if  the keyboard event file is somehow buffered and if there is any way to clean this file after every reading from this file? Maybe this could solve my problem that some characters are read multiple - 2 or 3 times.


Here is the code, that I used as a base of my application:





#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <errno.h>
#include <fcntl.h>
#include <dirent.h>
#include <linux/input.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/select.h>
#include <sys/time.h>
#include <termios.h>
#include <signal.h>
 
void handler (int sig)
{
  printf ("\nexiting...(%d)\n", sig);
  exit (0);
}
 
void perror_exit (char *error)
{
  perror (error);
  handler (9);
}
 
int main (int argc, char *argv[])
{
  struct input_event ev[64];
  int fd, rd, value, size = sizeof (struct input_event);
  char name[256] = "Unknown";
  char *device = NULL;
 
  //Setup check
  if (argv[1] == NULL){
      printf("Please specify (on the command line) the path to the dev event interface device\n");
      exit (0);
    }
 
  if ((getuid ()) != 0)
    printf ("You are not root! This may not work...\n");
 
  if (argc > 1)
    device = argv[1];
 
  //Open Device
  if ((fd = open (device, O_RDONLY)) == -1)
    printf ("%s is not a vaild device.\n", device);
 
  //Print Device Name
  ioctl (fd, EVIOCGNAME (sizeof (name)), name);
  printf ("Reading From : %s (%s)\n", device, name);
 
  while (1){
      if ((rd = read (fd, ev, size * 64)) < size)
          perror_exit ("read()");      
 
      value = ev[0].value;
 
      if (value != ' ' && ev[1].value == 1 && ev[1].type == 1){ // Only read the key press event
      printf ("Code[%d]\n", (ev[1].code));
      }
  }
 
  return 0;
}

---

