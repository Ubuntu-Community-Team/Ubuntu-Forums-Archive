---
title: "video recording in v4l"
date: 2011-02-19
forum: General Help
---

### Post by Vishnu V on 2011-02-19
Hi,
 I am trying to record video from my webcam using java (v4l). I got the following code for capture webcam
```

import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.io.IOException;
import java.nio.ByteBuffer;

import javax.swing.ImageIcon;
import javax.swing.JFrame;
import javax.swing.JLabel;

import au.edu.jcu.v4l4j.*;
import au.edu.jcu.v4l4j.exceptions.V4L4JException;
import au.edu.jcu.v4l4j.VideoDevice;
import au.edu.jcu.v4l4j.V4L4JConstants;

public class Viewer extends WindowAdapter implements Runnable {
        private VideoDevice vd;
        private JLabel l;
        private JFrame f;
        private long start = 0;
        private int n;
        private FrameGrabber fg;
        private Thread captureThread;
        private boolean stop;
        ByteBuffer bb;
        byte[] b;
        
        /**
         * Builds a WebcamViewer object
         * @param dev the video device file to capture from
         * @param w the desired capture width
         * @param h the desired capture height
         * @param std the capture standard
         * @param channel the capture channel
         * @param qty the JPEG compression quality
         * @throws V4L4JException if any parameter if invalid
         */
    public Viewer(String dev, int w, int h, int std, int channel, int qty) throws V4L4JException{
        initFrameGrabber(dev, w, h, std, channel, qty);
        initGUI();
        stop = false;
        captureThread = new Thread(this, "Capture Thread");
        captureThread.start();
    }
    
    /** 
     * Creates the graphical interface components and initialises them
     */
    private void initGUI(){
        f = new JFrame();
        l = new JLabel();
        f.getContentPane().add(l);
        f.setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        f.addWindowListener(this);
        f.setVisible(true);
        f.setSize(fg.getWidth(), fg.getHeight());       
    }
    
    /**
     * Initialises the FrameGrabber object with the given parameters
         * @param dev the video device file to capture from
         * @param w the desired capture width
         * @param h the desired capture height
         * @param std the capture standard
         * @param channel the capture channel
         * @param qty the JPEG compression quality
         * @throws V4L4JException if any parameter if invalid
     */
    private void initFrameGrabber(String dev, int w, int h, int std, int channel, int qty) throws V4L4JException{
    	
        vd = new VideoDevice(dev);
        fg = vd.getJPEGFrameGrabber(w, h, channel, std, qty);
        fg.startCapture();
        System.out.println("Starting capture at "+fg.getWidth()+"x"+fg.getHeight());            
    }
    
    /**
     * Updates the image shown in the JLabel
     * @param b
     */
    public void setImage(byte[] b) {
        l.setIcon(new ImageIcon(b));
    }
    
    /**
     * Implements the capture thread: get a frame from the FrameGrabber, and display it
     */
    public void run(){
        ByteBuffer bb;
        byte[] b;
        try {                   
                while(!stop){
                        bb = fg.getFrame();
                        b = new byte[bb.limit()];
                        bb.get(b);
                        setImage(b);
                }
        } catch (V4L4JException e) {
                e.printStackTrace();
                System.out.println("Failed to capture image");
        }
    }

    /**
     * Catch window closing event so we can free up resources before exiting
     * @param e
     */
        public void windowClosing(WindowEvent e) {
                if(captureThread.isAlive()){
                        stop = true;
                        try {
                                captureThread.join();
                        } catch (InterruptedException e1) {}
                }
                
                fg.stopCapture();
                vd.releaseFrameGrabber();
                
                f.dispose();            
        }
        


        public static void main(String[] args) throws V4L4JException, IOException {

                String dev = "/dev/video0";
                int w=640, h=480, std=V4L4JConstants.STANDARD_WEBCAM, channel = 0, qty = 60;
                new Viewer(dev,w,h,std,channel,qty);
        }
}

```
Please help me to record video

Thank you
vishnu v

---

### Post by no2498 on 2011-02-19
as i see it v4l is now part of v4l2 now days
may be why your having problems
just pointing

---

### Post by djails on 2011-03-06
You should ask for help on the v4l4j mailing list.

---

