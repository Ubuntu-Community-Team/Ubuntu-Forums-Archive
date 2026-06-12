---
title: "CLIENT &amp; SERVER  Chat PROGRAM"
date: 2009-12-05
forum: General Help
---

### Post by ZuzooVn on 2009-12-05
Hi every one. I have a question for you. This code below is the Client & server progam which can be a simple chat program in Ubuntu.

Code of server: receiverprog.c

```
    /*receiverprog.c - a server, datagram sockets*/

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <errno.h>
    #include <string.h>
    #include <sys/types.h>
    #include <sys/socket.h>
    #include <netinet/in.h>
    #include <arpa/inet.h>

    /* the port users will be connecting to */
    #define MYPORT 4950
    /* */
    #define MAXBUFLEN 500
     
    int main(int argc, char *argv[])
    {
        int sockfd;  
        /* my address information */
    
        struct sockaddr_in my_addr;
        /* connector’s address information */
    
        struct sockaddr_in their_addr;
    
        int addr_len, numbytes;
    
        char buf[MAXBUFLEN];
    
        if((sockfd = socket(AF_INET, SOCK_DGRAM, 0)) == -1)  
        {
            perror("Server-socket() sockfd error lol!");
    
            exit(1);
        }
    
        else
            printf("Server-socket() sockfd is OK...\n");
    
        /* host byte order */
        my_addr.sin_family = AF_INET;
    
        /* short, network byte order */
        my_addr.sin_port = htons(MYPORT);
    
        /* automatically fill with my IP */
        my_addr.sin_addr.s_addr = INADDR_ANY;
    
        /* zero the rest of the struct */
        memset(&(my_addr.sin_zero), '\0', 8);
    
        if(bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) == -1)
        {
            perror("Server-bind() error lol!");
            exit(1);
        }
        else
            printf("Server-bind() is OK...\n");
    
        addr_len = sizeof(struct sockaddr);
    
        if((numbytes = recvfrom(sockfd, buf, MAXBUFLEN-1, 0, (struct sockaddr *)&their_addr, &addr_len)) == -1)
        {
            perror("Server-recvfrom() error lol!");
            /*If something wrong, just exit lol...*/
            exit(1);
        }
    
        else
        {
            printf("Server-Waiting and listening...\n"); 
            printf("Server-recvfrom() is OK...\n");
        }
    
        printf("Server-Got packet from %s\n", inet_ntoa(their_addr.sin_addr));
        printf("Server-Packet is %d bytes long\n", numbytes);  
        buf[numbytes] = '\0'; 
        printf("Server-Packet contains \"%s\"\n", buf); 
        if(close(sockfd) != 0)  
            printf("Server-sockfd closing failed!\n");
    
        else
    
            printf("Server-sockfd successfully closed!\n");
    
        return 0;

    }

```Code of client: 

```
    /*senderprog.c - a client, datagram*/

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>
    #include <errno.h>
    #include <string.h>
    #include <sys/types.h>
    #include <sys/socket.h>
    #include <netinet/in.h>
    #include <arpa/inet.h>
    #include <netdb.h>
    /* the port users will be connecting to */
    #define MYPORT 4950
    
    int main(int argc, char *argv[ ])
    {

    int sockfd;

    /* connector’s address information */

    struct sockaddr_in their_addr;

    struct hostent *he;

    int numbytes;

     

    if (argc != 3)

    {

    fprintf(stderr, "Client-Usage: %s <hostname> <message>\n", argv[0]);

    exit(1);

    }

    /* get the host info */

    if ((he = gethostbyname(argv[1])) == NULL)

    {

    perror("Client-gethostbyname() error lol!");

    exit(1);

    }

    else

    printf("Client-gethostname() is OK...\n");

     

    if((sockfd = socket(AF_INET, SOCK_DGRAM, 0)) == -1)

    {

    perror("Client-socket() error lol!");

    exit(1);

    }

    else

    printf("Client-socket() sockfd is OK...\n");

     

    /* host byte order */

    their_addr.sin_family = AF_INET;

    /* short, network byte order */

    printf("Using port: 4950\n");

    their_addr.sin_port = htons(MYPORT);

    their_addr.sin_addr = *((struct in_addr *)he->h_addr);

    /* zero the rest of the struct */

    memset(&(their_addr.sin_zero), '\0', 8);

     

    if((numbytes = sendto(sockfd, argv[2], strlen(argv[2]), 0, (struct sockaddr *)&their_addr, sizeof(struct sockaddr))) == -1)

    {

    perror("Client-sendto() error lol!");

    exit(1);

    }

    else

    printf("Client-sendto() is OK...\n");

     

    printf("sent %d bytes to %s\n", numbytes, inet_ntoa(their_addr.sin_addr));

     

    if (close(sockfd) != 0)

    printf("Client-sockfd closing is failed!\n");

    else

    printf("Client-sockfd successfully closed!\n");

    return 0;

    }

```Would you please tell me which the protocol (UDP, TCP) has been used in this code and show how some important code sections work :popcorn:

Thanks you very much

I look forward to hearing from you.

---

### Post by ZuzooVn on 2009-12-05
Help me please. Thank you very much !

---

