**CS50x 2020 - Final Project**\
*Made by Samad, Colombo Sri Lanka*

In Sri Lanka we have a flourishing second hand mobile phone market. A lot of people buy used phones and sell them for a profit. One of my friends is also a part of this market. There is a major problem with this market, when a person buys a used phone they have no way of checking if the phone is stolen. The phones that are bought/resold in this market are done without any paperwork and just by word of mouth so there is always a risk of buying a stolen phone, which brings legal trouble later on.

A few months back, before I started CS50x, my friend asked me if I knew someone who could make a website to help tackle this problem. This is the reason that I chose this idea as my final project.

The idea is simple, anyone who loses their mobile phone can come to the website and submit the details of the lost device. At this point the report has to verified by an Admin of the website, by calling the user with the details provided to ensure everything is proper. If the Admin decides to reject the report he has to give a reason. If the Admin approves the report the reported device is live on the website. Anyone can now lookup this device by providing its IMEI.

At any point if the device has been found the user can contact the website Admin over the phone and the Admin can remove the device from the website.

The website has the following sections,


**USER END**

*Index*\
-Just shows the basic idea of the website.

*Lookup IMEI*\
-Entering a valid IMEI will show if the device has been reported as stolen and the details of the person who reported it.

*Report Lost Device*\
-You can submit a lost device here by providing your details and the device details. After successful admin verification it will be added to the website. If someone else has already reported a similar IMEI it will show you that as well.

*Check Status*\
-You can check the status of the report you submitted. It shows if the report is pending, has been accepted or rejected.

*Admin Login*\
-Allows an admin to login.

*API*\
-Allows anyone to lookup a device by sending a POST request with valid IMEI number.


**ADMIN END**

*Pending Reports*\
-This section lists all the reports pending verification. If an admin chooses to reject a report the admin has to provide a reason, which will be shown when a user who submitted the report checks the website to see the status of his report.

*Search Reports*\
-The admin can lookup an active report/reports using the mobile number (multiple reports can be submitted for the same number) or the IMEI (only one report can be active for a unique IMEI). The admin can then choose to deactivate an active report if the device has been found, after confirmation the report is marked as found and deactivated i.e. it is no longer visible on the website when searched.

*Stats*\
-This page shows a basic list of stats which contains the number of,
1. Reports submitted within the current day.
2. Reports submitted within the current month.
3. Reports waiting verification.
4. Reports that are active.
5. Reports that have been marked as found (device has been found).

*Admins*\
-This page can only be accessed by super admins, if a normal admin tries to access this page an error is shown. A super admin can add new Admins to the system and choose if they will be normal admins or super admins. The only difference between the two categories is that super admins can manage the Admins section. A list is shown when this page is accessed which lists all admins (except the logged in admin), using this list a super admin can remove any other admin from the system.

*Change Password*\
-Allows the admin to change their password.


*Major validations done*
1. Ensuring that all fields are filled using HTML and Python (for bad actors)
2. Ensuring that the IMEI number entered is valid by checking if it is a number, is 15 characters long and that itconforms to Luhn's algorithm
3. Ensuring that the mobile number entered is valid by checking if it is a number and 10 characters long.
4. Ensuring that a similar IMEI isnt submitted twice if it is currently awaiting admin verification or if it is active on the site. This also applies if another user has submitted the same IMEI and matches the conditions stated earlier. If the report is longer active or the report has been rejected for some reason the IMEI can be submitted again.
5. Ensuring the Admin has to confirm the report Approval/Rejection/Found by using some Javascript.
6. Ensuring that if a bad actor sends invalid values for (by modifying the HTML element before submitting the form) report approval/rejection it is rejected
7. Ensuring only super admins can access the Admins page for admin management.
8. Ensuring that the currently logged in admin cannot remove that account for managing admins.
9. Ensuring that the passwords match and are not equal to the old password when the password is changed.
10. Ensuring the system doesn't show an error if the imei is field is not included in an API request.
