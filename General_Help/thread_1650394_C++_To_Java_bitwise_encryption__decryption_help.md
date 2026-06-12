---
title: "C++ To Java bitwise encryption / decryption help"
date: 2010-12-21
forum: General Help
---

### Post by =Fallen= on 2010-12-21
Hi everybody, i'm having issues with my code (i'm kinda new to java).
I'm trying to convert a c++ code snippet to java in order to use it in my application.

Here's the C++ code
```

#ifndef _ENCRYPTOR_H_
#define _ENCRYPTOR_H_
#include <stdio.h>
#include <stdlib.h>
#include "../Base/inc/SvrBase.h"
#include "../Base/inc/Heap.h"
namespace snet
{
    class IEncryptor
    {
    public:
        // The release of the encryption interface
        virtual unsigned long    Release            (void)                            = 0;

        // Specified length of encrypted data
        virtual void            Encrypt            (unsigned char* buf, int nLen)    = 0;

        // Decrypt the data according to specified length    
        virtual void            Decrypt            (unsigned char* buf, int nLen)    = 0;

        // This method can be re-specified length of the decrypted data encryption and decryption to return to the state before
        virtual void            Rencrypt        (unsigned char* buf, int nLen)    = 0;

        // Change the cipher code
        virtual void            ChangeCode        (unsigned long ulCode)            = 0;
        virtual void            ChangeCode        (const char* pszKey)            = 0;

        // Generate a new encryption interface
        virtual IEncryptor*        Duplicate        (void)                            = 0;

        virtual void            Refresh         ()                              = 0;
    };
 ////////////////////////////////////////////////////////////////////////////////////////////////////
    // Three random numbers, used to hide in the server INI SERVER KEY. Unchanged
    ////////////////////////////////////////////////////////////////////////////////////////////////////
    #define        aa    0x7E // its 126
    #define        bb    0x33 // It's the number 33
    #define        cc    0xA1 // It's 161


    //#define ENCRYPT_KEY1                0xa61fce5e    
// A = 0x20, B = 0xFD, C = 0x07, first = 0x1F, key = a61fce5e
    //#define ENCRYPT_KEY2                0x443ffc04    
// A = 0x7A, B = 0xCF, C = 0xE5, first = 0x3F, key = 443ffc04

    template<unsigned long key1, unsigned long key2>
    class TEncryptServer : public IEncryptor
    {
    public:
        TEncryptServer()        { this->Init(); }
    public:
        virtual void            ChangeCode    (DWORD dwData);
        virtual void            ChangeCode    (const char* pszKey);

        virtual void            Encrypt        (unsigned char * bufMsg, int nLen);
        virtual void            Decrypt        (unsigned char* buf, int nLen);
        virtual void            Rencrypt    (unsigned char* , int )        { return; }

        virtual IEncryptor*        Duplicate    (void)                                { return new TEncryptServer; }
        virtual unsigned long    Release        (void)                                { delete this; return 0; }
        virtual void            Refresh     (void)                              { m_nPos1 = m_nPos2 = m_nPos3 = m_nPos4 = 0; }

    protected:
        void            Init        (void);
        int                m_nPos1;
        int                m_nPos2;

        int             m_nPos3;
        int             m_nPos4;

    private:
        unsigned char m_bufEncrypt1[256];
        unsigned char m_bufEncrypt2[256];

    public:
        //MYHEAP_DECLARATION(s_heap)
    };

    //template<unsigned long key1, unsigned long key2>
    //sbase::CHeap TEncryptServer<key1, key2>::s_heap;

    //template <unsigned long key1, unsigned long key2>
    //TEncryptServer<key1, key2>::CEncryptCode    TEncryptServer<key1, key2>::m_cGlobalEncrypt;

    template<unsigned long key1, unsigned long key2>
    inline void 
        TEncryptServer<key1, key2>::Init(void)
    {
        m_nPos1 = m_nPos2 = 0;
        m_nPos3 = m_nPos4 = 0;

        try{
            // Generate ABC
            int    a1, b1, c1, fst1;
            a1        = ((key1 >> 0) & 0xFF) ^ aa;
            b1        = ((key1 >> 8) & 0xFF) ^ bb;
            c1        = ((key1 >> 24) & 0xFF) ^ cc;
            fst1    = (key1 >> 16) & 0xFF;

            int    a2, b2, c2, fst2;
            a2        = ((key2 >> 0) & 0xFF) ^ aa;
            b2        = ((key2 >> 8) & 0xFF) ^ bb;
            c2        = ((key2 >> 24) & 0xFF) ^ cc;
            fst2    = (key2 >> 16) & 0xFF;

            unsigned char    nCode = (unsigned char)fst1;
            for(int i = 0; i < 256; i++)
            {
                m_bufEncrypt1[i] = nCode;
                //printf("%02X ", nCode);
                nCode = (unsigned char)(a1*nCode*nCode + b1*nCode + c1) % 256;
            }
            //printf("[%02X]\n", nCode);
            ASSERT(nCode == fst1);

            nCode = (unsigned char)fst2;
            for(int  i = 0; i < 256; i++)
            {
                m_bufEncrypt2[i] = nCode;
                nCode = (unsigned char)(a2*nCode*nCode + b2*nCode + c2) % 256;
            }
            ASSERT(nCode == fst2);
        }catch(...){ sbase::LogSave("Net", "Encryptor init fail."); }
    }


    template<unsigned long key1, unsigned long key2>
    inline void 
        TEncryptServer<key1, key2>::Encrypt(unsigned char * bufMsg, int nLen)
    {
        bool bMove = true;
        try{
            int        nOldPos1 = m_nPos1;
            int        nOldPos2 = m_nPos2;

            for(int i = 0; i < nLen; i++)
            {
                // CQ AccountServer Unique
                //bufMsg[i] ^= 0xab;
                //int a = (bufMsg[i]&0x0f)*0x10;
                //int b = (bufMsg[i]&0xf0)/0x10;
                //bufMsg[i] = (unsigned char)(a + b);

                bufMsg[i] ^= m_bufEncrypt1[m_nPos1];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos2];

                if(++m_nPos1 >= 256)
                    m_nPos1 = 0;

                if(++m_nPos2 >= 256)
                    m_nPos2 = 0;

                assert(m_nPos1 >=0 && m_nPos1 < 256);
                assert(m_nPos2 >=0 && m_nPos2 < 256);
            }

            if(!bMove)
            {
                // Restore pointer
                m_nPos1 = nOldPos1;
                m_nPos2 = nOldPos2;
            }
        }catch(...){  printf("Encryptor Encrypt fail."); }
    }

    template<unsigned long key1, unsigned long key2>
    inline void TEncryptServer<key1, key2>::Decrypt(unsigned char * bufMsg, int nLen)
    {
        bool bMove = true;
        try{
            int        nOldPos1 = m_nPos3;
            int        nOldPos2 = m_nPos4;
            for(int i = 0; i < nLen; i++)
            {
                bufMsg[i] ^= m_bufEncrypt1[m_nPos3];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos4];
                if(++m_nPos3 >= 256)
                    m_nPos3 = 0;

                if(++m_nPos4 >= 256)
                    m_nPos4 = 0;

                assert(m_nPos3 >=0 && m_nPos3 < 256);
                assert(m_nPos4 >=0 && m_nPos4 < 256);
            }

            if(!bMove)
            {
                // Restore pointer
                m_nPos3 = nOldPos1;
                m_nPos4 = nOldPos2;
            }
        }catch(...){  printf("Encryptor Encrypt fail."); }
    }

    template<unsigned long key1, unsigned long key2>
    inline void TEncryptServer<key1, key2>::ChangeCode(DWORD dwData)
    {
        try{
            DWORD    dwData2 = dwData*dwData;
            for(int i = 0; i < 256; i += 4)
            {
                *(DWORD*)(&m_bufEncrypt1[i]) ^= dwData;
                *(DWORD*)(&m_bufEncrypt2[i]) ^= dwData2;
            }
        }catch(...){ sbase::LogSave("Net", "Encryptor ChangeCode fail."); }
    }

    template<unsigned long key1, unsigned long key2>
    inline void 
        TEncryptServer<key1, key2>::ChangeCode(const char* pszKey)
    {
        if (!pszKey)
            return;

        try{
            DWORD dwData = (DWORD) atoi(pszKey);

            DWORD    dwData2 = dwData*dwData;
            for(int i = 0; i < 256; i += 4)
            {
                *(DWORD*)(&m_bufEncrypt1[i]) ^= dwData;
                *(DWORD*)(&m_bufEncrypt2[i]) ^= dwData2;
            }
        }catch(...){ sbase::LogSave("Net", "Encryptor ChangeCode fail."); }
    }
}

#endif 



```**And here's the java code:**

---

### Post by =Fallen= on 2010-12-21
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package gwohepsilon;

/**
 *
 * @author Christian
 */
public class functions {
    //################################################################################################################
class snet
{

    ////////////////////////////////////////////////////////////////////////////////////////////////////
    // Three random numbers, used to hide in the server INI SERVER KEY. Unchanged
    ////////////////////////////////////////////////////////////////////////////////////////////////////
                public static final int                 aa    =0x7E; // its 126
                public static final int                 bb    =0x33; // It's the number 33
                public static final int                 cc    =0xA1; // It's 161
                public static final int                 A       =0x20;  
                public static final int                 A1      =0x7A; 
                public static final int                 B       =0xFD; 
                public static final int                 B1      =0xCF;
                public static final int                 C       =0x07; 
                public static final int                 C1      =0xE5; 
                public static final int                 F       =0x1F; 
                public static final int                 F1      =0x3F; 
                public static final int                 K       =0xA61fCE5E; 
                public static final int                 K1      =0x443FFC04; 
                public static final int                 key1    =0xa61fce5e; 
                public static final int                 key2    =0x443ffc04; 
                int m_nPos1, m_nPos2, m_nPos3, m_nPos4 = 0;
        char[] m_bufEncrypt1,m_bufEncrypt2 = new char[256];
                char[] bufMsg = "&#65533;&#65533;&#65533;&W&#65533;_7&#65533;&#65533;&#65533;&#65533;&#65533;V &#65533;F`&#65533;d&#65533;";
                int nLen = bufMsg.length;
            // Generate ABC
            int    a1, b1, c1, fst1;
            int a1()  { return ((key1 >> 0) & 0xFF) ^ aa; }
            int b1()  { return ((key1 >> 8) & 0xFF) ^ bb; }
            int c1()  { return ((key1 >> 24) & 0xFF) ^ cc;}
            int fst1(){ return (key1 >> 16) & 0xFF;       }
            int    a2, b2, c2, fst2;
            int a2()  { return ((key2 >> 0) & 0xFF) ^ aa;   }
            int b2()  { return ((key2 >> 8) & 0xFF) ^ bb;   }
            int c2()  { return ((key2 >> 24) & 0xFF) ^ cc;  }
            int fst2(){ return (key2 >> 16) & 0xFF;         }

char nCode(){
char    nCode = (char)fst1;
for(int i = 0;i < 256; i++)
{
m_bufEncrypt1[i] = nCode;
System.out.printf("%02X ", nCode);
nCode = (char)((a1*nCode*nCode + b1*nCode + c1) % 256);
}
return nCode;
}
char nCode2(){
//printf("[%02X]\n", nCode);
char nCode = (char)fst2;
for(int  i = 0; i < 256; i++)
{
m_bufEncrypt2[i] = nCode;
nCode = (char)((a2*nCode*nCode + b2*nCode + c2) % 256);
}
return nCode;
}
void Encrypt(char bufMsg[]){
                boolean bMove = true;
        try{int        nOldPos1 = m_nPos1;int        nOldPos2 = m_nPos2;
            for(int i = 0; i < nLen; i++){
                bufMsg[i] ^= m_bufEncrypt1[m_nPos1];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos2];
                if(++m_nPos1 >= 256)m_nPos1 = 0;
                if(++m_nPos2 >= 256)m_nPos2 = 0;
                assert(m_nPos1 >=0 && m_nPos1 < 256);
                assert(m_nPos2 >=0 && m_nPos2 < 256);
            }
                System.out.println("[Message]: "+bufMsg);
        }catch(Exception err){  System.out.println("[SEX]: "+err); }
    }
void Decrypt(){
    
        boolean bMove = true;
        try{int        nOldPos1 = m_nPos3;int        nOldPos2 = m_nPos4;
            for(int i = 0; i < nLen; i++)
            {
                bufMsg[i] ^= m_bufEncrypt1[m_nPos3];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos4];
                if(++m_nPos3 >= 256)m_nPos3 = 0;
                if(++m_nPos4 >= 256)m_nPos4 = 0;
                assert(m_nPos3 >=0 && m_nPos3 < 256);
                assert(m_nPos4 >=0 && m_nPos4 < 256);
            }
        }catch(Exception e){  System.out.println("Encryptor Encrypt fail."+e); }
}
}// End of snet
}// End of public class functions
//###############################################################################################################
```The thing is ,that, the java version of the code won't work. So here I am.

---

### Post by Spyderkid on 2010-12-21
if you need to compile it first you need to run this to install the compiler....

```

sudo apt-get install build-essential

```


Then cd to the directory which the file is in and run this replacing input with the file name and output with what you want it to be called afterwards.

```

g++ input.cpp -o output

```


[SIZE="4"][B][COLOR="Red"]NOTE:
/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\
 YOU MUST SAVE THE FILE WITH .CPP ON THE END SO YOU CAN COMPILE IT
\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/[/COLOR][/B][/SIZE]

---

### Post by =Fallen= on 2010-12-21
Well , the problem is not the compilation. It's the encryption/decryption algorithms that refuse to work (the java ones, the c++ code works fine).

Anyway, thanks for reply!

Here's my app:

[COLOR=Red][B]Main.java

[/B][/COLOR]> 
package gwohepsilon;

import java.net.*;
import java.io.*;

public class Main {
    public static void main(String[] args) {
        int port = 5999;
        try {
            ServerSocket server = new ServerSocket(port);
            while (true) {
                Socket sock = server.accept();
                System.err.println("[Connected to]: " + sock);
                new echo(sock);
            }
        }
        catch (IOException e) {
            e.printStackTrace();
        }
    }
}

class echo extends Thread {
    Socket sock;

    echo(Socket sock) {
        this.sock = sock;
        start();
    }
//IP=67.208.220.189
    public void run() {
        try {
            BufferedReader in  = new BufferedReader(new InputStreamReader(sock.getInputStream()));
            BufferedWriter out = new BufferedWriter(new OutputStreamWriter(sock.getOutputStream()));
            String s;
            while ((s = in.readLine()) != null) {
                System.out.println("[Client->Server]["+sock.getInetAddress()+"]:"+s);
                functions fn = new functions();
                functions.snet snet = fn.new snet();
                snet.Decrypt(s.toCharArray());
                if (s.equals("Exit"))
                    break;
                if (s.equals("Die!"))    // a way to kill the server
                    System.exit(0);
            }
            sock.close();
        }
        catch (IOException e) {
            System.err.println("[Server exception]: " + e);
        }
    }

}


[COLOR=Red]**Functions.java**[/COLOR]

> 
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package gwohepsilon;

/**
 *
 * @author Christian
 */
public class functions {
    //################################################################################################################
class snet
{

    ////////////////////////////////////////////////////////////////////////////////////////////////////
    // Three random numbers, used to hide in the server INI SERVER KEY. Unchanged
    ////////////////////////////////////////////////////////////////////////////////////////////////////
                public static final int                 aa    =0x7E; // its 126
                public static final int                 bb    =0x33; // It's the number 33
                public static final int                 cc    =0xA1; // It's 161
                public static final int                 A       =0x20;  
                public static final int                 A1      =0x7A; 
                public static final int                 B       =0xFD; 
                public static final int                 B1      =0xCF;
                public static final int                 C       =0x07; 
                public static final int                 C1      =0xE5; 
                public static final int                 F       =0x1F; 
                public static final int                 F1      =0x3F; 
                public static final int                 K       =0xA61fCE5E; 
                public static final int                 K1      =0x443FFC04; 
                public static final int                 key1    =0xa61fce5e; 
                public static final int                 key2    =0x443ffc04; 
                int m_nPos1, m_nPos2, m_nPos3, m_nPos4 = 0;
        char[] m_bufEncrypt1,m_bufEncrypt2 = new char[256];
               int nLen = bufMsg.length;
            // Generate ABC
            int    a1, b1, c1, fst1;
            int a1()  { return ((key1 >> 0) & 0xFF) ^ aa; }
            int b1()  { return ((key1 >> 8) & 0xFF) ^ bb; }
            int c1()  { return ((key1 >> 24) & 0xFF) ^ cc;}
            int fst1(){ return (key1 >> 16) & 0xFF;       }
            int    a2, b2, c2, fst2;
            int a2()  { return ((key2 >> 0) & 0xFF) ^ aa;   }
            int b2()  { return ((key2 >> 8) & 0xFF) ^ bb;   }
            int c2()  { return ((key2 >> 24) & 0xFF) ^ cc;  }
            int fst2(){ return (key2 >> 16) & 0xFF;         }

char nCode(){
char    nCode = (char)fst1;
for(int i = 0;i < 256; i++)
{
m_bufEncrypt1[i] = nCode;
System.out.printf("%02X ", nCode);
nCode = (char)((a1*nCode*nCode + b1*nCode + c1) % 256);
}
return nCode;
}
char nCode2(){
//printf("[%02X]\n", nCode);
char nCode = (char)fst2;
for(int  i = 0; i < 256; i++)
{
m_bufEncrypt2[i] = nCode;
nCode = (char)((a2*nCode*nCode + b2*nCode + c2) % 256);
}
return nCode;
}
void Encrypt(char bufMsg[]){
                boolean bMove = true;
        try{int        nOldPos1 = m_nPos1;int        nOldPos2 = m_nPos2;
            for(int i = 0; i < nLen; i++){
                bufMsg[i] ^= m_bufEncrypt1[m_nPos1];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos2];
                if(++m_nPos1 >= 256)m_nPos1 = 0;
                if(++m_nPos2 >= 256)m_nPos2 = 0;
                assert(m_nPos1 >=0 && m_nPos1 < 256);
                assert(m_nPos2 >=0 && m_nPos2 < 256);
            }
                System.out.println("[Message]: "+bufMsg);
        }catch(Exception err){  System.out.println("[SEX]: "+err); }
    }
void Decrypt(char bufMsg[]){
    
        boolean bMove = true;
        try{int        nOldPos1 = m_nPos3;int        nOldPos2 = m_nPos4;
            for(int i = 0; i < nLen; i++)
            {
                bufMsg[i] ^= m_bufEncrypt1[m_nPos3];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos4];
                if(++m_nPos3 >= 256)m_nPos3 = 0;
                if(++m_nPos4 >= 256)m_nPos4 = 0;
                assert(m_nPos3 >=0 && m_nPos3 < 256);
                assert(m_nPos4 >=0 && m_nPos4 < 256);
            }
        }catch(Exception e){  System.out.println("Encryptor Encrypt fail."+e); }
}
}// End of snet
}// End of public class functions
//###############################################################################################################
The output (netbeans)
> 
[Connected to]: Socket[addr=/127.0.0.1,port=4001,localport=5999]
[Client->Server][/127.0.0.1]:&#65533;&#65533;&#65533;&A&#65533;C"&#65533;&#65533;&#65533;&#65533;&#65533;V &#65533;F`&#65533;d&#65533;
Encryptor Encrypt fail.java.lang.NullPointerException
[Client->Server][/127.0.0.1]:&#65533;&#65533;&#65533;&#65533;+++++++++++
The problem is here: 

> void Decrypt(char bufMsg[]){
    
        boolean bMove = true;
        try{int        nOldPos1 = m_nPos3;int        nOldPos2 = m_nPos4;
            for(int i = 0; i < nLen; i++)
            {
                bufMsg[i] ^= m_bufEncrypt1[m_nPos3];
                bufMsg[i] ^= m_bufEncrypt2[m_nPos4];
                if(++m_nPos3 >= 256)m_nPos3 = 0;
                if(++m_nPos4 >= 256)m_nPos4 = 0;
                assert(m_nPos3 >=0 && m_nPos3 < 256);
                assert(m_nPos4 >=0 && m_nPos4 < 256);
            }
                System.out.println("[DECODE TEST]: "+ bufMsg);
        }catch(Exception e){  System.out.println("Encryptor Encrypt fail."+e); }
}Catch returns a null pointer exception , what does that mean?

---

### Post by =Fallen= on 2010-12-22
bump?

still nothing?

---

