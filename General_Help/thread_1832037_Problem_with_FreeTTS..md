---
title: "Problem with FreeTTS."
date: 2011-08-24
forum: General Help
---

### Post by soyio on 2011-08-24
Hi there.
i m running a sample project on netbeans and i m using freetts to output some voice.
While running it inside netbeans it works fine..
When i try to run it from the dist folder that netbeans create, i get this error...
```

Using voice: kevin16
testing 1
java.util.zip.ZipException: error in opening zip file
    at java.util.zip.ZipFile.open(Native Method)
    at java.util.zip.ZipFile.<init>(ZipFile.java:127)
    at java.util.jar.JarFile.<init>(JarFile.java:135)
    at java.util.jar.JarFile.<init>(JarFile.java:72)
    at sun.net.www.protocol.jar.URLJarFile.<init>(URLJarFile.java:72)
    at sun.net.www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:48)
    at sun.net.www.protocol.jar.JarFileFactory.get(JarFileFactory.java:55)
    at sun.net.www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:104)
    at sun.net.www.protocol.jar.JarURLConnection.getJarFile(JarURLConnection.java:71)
    at java.net.JarURLConnection.getManifest(JarURLConnection.java:217)
    at java.net.JarURLConnection.getMainAttributes(JarURLConnection.java:269)
    at com.sun.speech.freetts.VoiceManager.getDependencyURLs(VoiceManager.java:251)
    at com.sun.speech.freetts.VoiceManager.getDependencyURLs(VoiceManager.java:283)
    at com.sun.speech.freetts.VoiceManager.getVoiceDirectories(VoiceManager.java:173)
    at com.sun.speech.freetts.VoiceManager.getVoices(VoiceManager.java:110)
    at com.sun.speech.freetts.VoiceManager.getVoice(VoiceManager.java:502)
    at javaapplication11.JavaApplication11.main(JavaApplication11.java:22)
System property "mbrola.base" is undefined.  Will not use MBROLA voices.
testing 2
Cannot find a voice named kevin16.  Please specify a different voice.

```here is the code where the error is coming from (particularly between the testing1-testing2 print statements)

```
package javaapplication11;
import com.sun.speech.freetts.Voice;
import com.sun.speech.freetts.VoiceManager;

public class JavaApplication11 {

    public static void main(String[] args) {
        // TODO code application logic here
      String voiceName = (args.length > 0)
            ? args[0]
            : "kevin16";
        System.out.println();
        System.out.println("Using voice: " + voiceName);
        /* The VoiceManager manages all the voices for FreeTTS.
         */
        VoiceManager voiceManager = VoiceManager.getInstance();

        System.out.println("testing 1");
        Voice helloVoice = voiceManager.getVoice(voiceName);
        System.out.println("testing 2");

        if (helloVoice == null) {
            System.err.println(
                "Cannot find a voice named "
                + voiceName + ".  Please specify a different voice.");
        }
        else{
        helloVoice.allocate();
        /* Synthesize speech.
         */
        helloVoice.speak("Thank you for giving me a voice. "
                         + "I'm so glad to say hello to this world.");
        /* Clean up and leave.
         */
        helloVoice.deallocate();
        }
    }
}
```
Any ideas why this is happening? i tried a lot to find why but didn't make it...
Thank you

---

