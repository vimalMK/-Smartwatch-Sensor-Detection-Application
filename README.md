# -Smartwatch-Sensor-Detection-Application
NodeJs/ Apache Cordova/ Java/ J2ME -


In this application, we use a Microsoft Band smartwatch and an Android smartphone to detect fall. This application is written purely in Java. The architecture of a native Android application in Java for Fall Detection is shown below in figure 5.1.1 
We used Android Studio to develop this application. The Android platform version used is 7.0. The Microsoft Band smartwatch is used to collect sensor data’s and render it on the Android App running on the smartphone.  As shown in Figure 5.1.1, the whole application is written in Java and interacting with the Microsoft MS Band SDK. The Microsoft MS Band SDK is a jar file which has to be included in the application library. The Fall Detection application relies on  WEKA’s machine learning algorithm  to predict the fall.
 
 ![alt text](https://github.com/vimalMK/Fall-Detection-Application-Using-Microsoft-Band-Watch/blob/master/Arc.jpg)


	 Fig 5.1.1 Native Android Application in java for Fall Detection

WEKA  (Waikato Environment for Knowledge Analysis)  is a suite of machine learning software written in Java, developed at the University of Waikato, New Zealand. It is a free software licensed under the GNU General Public License [14]. WEKA contains visualizations tools and various machine learning algorithms, which help in data analysis and predictive modeling [15]. The fall detection application uses Support Vector Machines (SVM) to train the fall detection model.
As discussed earlier, MainActivity.java is the entry point of this application. The MainActivity.java loads the layout and other dependent classes to be imported into the application. Figure 5.1.2 represents the folder structure of the native Android application in Java for Fall Detection. 

  ![alt text](https://github.com/vimalMK/Fall-Detection-Application-Using-Microsoft-Band-Watch/blob/master/Arc1.jpg)


                                   Fig 5.1.2 Native Android Application in java for Fall Detection 

The Native Android application in Java for Fall Detection has different packages such as sensors, sensors_local, sensors_msband and sensors_persistence under the main package reuiot2015.smartwatch. These packages contain Java classes which are responsible for connecting to the smartwatch, access the sensor data from the smartwatch and retrieve the data value for each sensor. The main data collected from the smartwatch for the Fall Detection application are the accelerometer sensor data. 
The main java class responsible for detecting FALL / NO FALL is the prediction class. The prediction class reads in a trained model named ‘fallsvmmodel.model’ and for the data values collected from the smartwatch, it checks against the trained model to predict FALL / NO FALL. 
For every 0.25 seconds approximately, the accelerometer sensor value is captured, and the prediction for FALL /NO FALL is done and stored along with the sensor data value in the CSV file. This is called internal prediction. The final prediction is detected in a sliding window of 3 seconds. In that 3 seconds, if FALL are predicted in a sequence between 2 and 5, the final prediction is a FALL, otherwise, it is a NOT Fall.
