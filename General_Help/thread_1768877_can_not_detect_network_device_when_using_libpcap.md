---
title: "can not detect network device when using libpcap"
date: 2011-05-27
forum: General Help
---

### Post by contau on 2011-05-27
Hi all,
I use libpcap to write a program to detect network device in Ubuntu but not sucess. The result is no suitable device found. How many reasons are there for that? please help? The code i used is the main user page.
[code]
#define HAVE_REMOTE
#define WPCAP
#include <pcap.h>
#include <stdlib.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main()
{
    pcap_if_t *alldevs;
    pcap_if_t *d;
    int i=0;
    char errbuf[PCAP_ERRBUF_SIZE];
    
    /* Retrieve the device list from the local machine */
    if (pcap_findalldevs(&alldevs, errbuf) == -1)
    {
        fprintf(stderr,"Error in pcap_findalldevs  %s\n", errbuf);
        exit(1);
    }
    
    /* Print the list */
    for(d= alldevs; d != NULL; d= d->next)
    {
        printf("%d. %s", ++i, d->name);
        if (d->description)
            printf(" (%s)\n", d->description);
        else
            printf(" (No description available)\n");
    }
    
    if (i == 0)
    {
        printf("\nNo interfaces found!\n");
        return (1);
    }
    pcap_freealldevs(alldevs);
    return 0;
}
{/code]

---

### Post by contau on 2011-05-27
can anybody help me pls ?

---

### Post by webofunni on 2011-05-27
That programs seems to be working in my system. 

```

root@ubuntu-server:~# gcc pac.c -lpcap -o output
root@ubuntu-server:~# ./output 
1. eth1 (No description available)
2. usbmon1 (USB bus number 1)
3. eth2 (No description available)
4. any (Pseudo-device that captures on all interfaces)
5. lo (No description available)
root@ubuntu-server:~# 

```

---

### Post by contau on 2011-05-27
Thank for ur answer. I found out the error.

---

### Post by contau on 2011-05-27
I also have a new problam that is the pcap_findalldevs_ex is undefined function . I defined #HAVE_REMOTE but not complete. i don't understand why? pls help

---

