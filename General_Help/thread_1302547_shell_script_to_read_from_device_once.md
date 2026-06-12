---
title: "shell script to read from device once"
date: 2009-10-27
forum: General Help
---

### Post by skaldyr on 2009-10-27
I have a device that sends out data when there is a change, in this case its signal strength of a modem.

i need to make a shell script that reads the device for 3 seconds once then writes out the first line and closes. how could this be done?

i have so far used 

```
grep RSSI /dev/ttyUSB1 stty
```

but i dont know how to stop it after 3 seconds and the only write out the first line.

---

### Post by Giblet5 on 2009-10-27
You can use minicom with runscript...

Have you taken a look at [umtsmon]("http://umtsmon.sourceforge.net/")?

---

### Post by skaldyr on 2009-10-27
I need it to be a simple shell script with output to the terminal because im using the result in a c++ programme.

---

### Post by Giblet5 on 2009-10-27
> **skaldyr said:**
> I need it to be a simple shell script with output to the terminal because im using the result in a c++ programme.

Then why don't you just open the device in raw mode and use a SIGALRM handler to read the data?

Read signal(3C) man page.

Calling a shell script from C++ is like fueling a Bugatti Veyron with used deep-fry oil. ;)


```
...

void _sigalrm( int sig )
{
    // handle the exception
}

char * QueuedRead( const char *ttyname, int seconds )
{
    int ttyfd;
    static char bp[32];

    memset(bp, 0, 32);
    ttyfd = open(ttyname, O_RDONLY);
    signal(SIGALRM, _sigalrm);
    alarm(seconds);
    read(ttyfd, bp, 32);
    close(ttyfd);
    return(bp);
}
...

    // Open the terminal, attempt read for at-most 3 seconds
    char *p = QueuedRead("/dev/ttyS0", 3);
    if (strlen(p)) {
        // Hey Mo! It woiked!
    } else {
        // It failed. That modem sucks.
    }
```

---

### Post by skaldyr on 2009-10-27
Thanks man. I will try that. 

You most have been real bored. Lucky for me.



the only thing am not sure about is the sigalrm()

---

### Post by skaldyr on 2009-10-27
what does the _sigalrm function do?

i added void in front of the sigalrm to make it compile right.

when i run main the only thing returned in p is a space

---

### Post by Giblet5 on 2009-10-27
Yes... void was missing...


_sigalarm is just a function to divert the SIGALRM signal to. It doesn't have to do anything.

When the alarm times out, your program will receive the signal and that blocking read will return immediately whether data was read or not.

The read() call will return -1 if it timed out first and the array will still be zeroed out (strlen() returns zero).

Elegant and quick.

You can eliminate the blocking completely by using select() with a suitable timeout and periodically polling the file descriptor for ready data...but that way lies madness if you're new to select(2).

---

### Post by Giblet5 on 2009-10-27
> **skaldyr said:**
> what does the _sigalrm function do?

i added void in front of the sigalrm to make it compile right.

[COLOR="DarkRed"]when i run main the only thing returned in p is a space[/COLOR]

Meh. It's too fast...

Serial ports are slow.

Try reading one character into the buffer at a time, until you get a linefeed or carriage return, like replacing the single read with:
```
...
    int index = 0;
    while(read(ttyfd, &bp[index], 1) == 1) {
        if(bp[index] == '\n' || bp[index] == '\r') break;
        ++index;
    }
...
```

Of course, you'll have to alter the success test to handle partial results...

---

### Post by Giblet5 on 2009-10-27
As I stated earler, I'm bored.

Give me an example of the output string you expect and I'll post a function to read it or time out and indicate an error.

---

### Post by skaldyr on 2009-10-28
the problem is that it's pretty random what comes out of the modem. here's an example of the output:

```
^BOOT:95216501,0,0,0,6



^DSFLOWRPT:000004EA,00000000,00000000,0000000000057EE7,00000000000AEC7C,0000BB80,00046500



^DSFLOWRPT:000004EC,00000000,00000000,0000000000057EE7,00000000000AEC7C,0000BB80,00046500



^DSFLOWRPT:000004EE,00000000,00000000,0000000000057EE7,00000000000AEC7C,0000BB80,00046500


^RSSI:12
```it cant be predicted when the RSSI: will appear. there might be 5 DSFLOWRPT outputs or 10 and some BOOT and maybe a MODE.

---

