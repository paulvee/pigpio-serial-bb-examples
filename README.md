# pigpio-serial-bb-examples
pigpio serial bit-banging examples

The pigpio library (http://abyz.me.uk/rpi/pigpio/index.html) used on a Raspberry Pi contains code that allows you to manipulate the GPIO pins with a C or Python script. There are functions in the libary that can provide the equivalent of Arduino-like soft_serial functionality, that allow you to get more serial UART functionality. The RPi only provides one "real" serial UART port, but if you need more UART's, the pigpio library can be used to turn just about any GPIO pin into a serial RxT or TxD functionality.

I needed two additional UART's and used the Python bb_serial_read() function of the library to create two more RxD ports that can capture serial data.  
The examples provided read the serial data from an Arduino based counter, that sends results every 1,000 or 10,000 seconds, and the NMEA stream coming from a U-Blox GPS module.

Both devices send out complete ASCII strings, but the bb_serial_read() function captures data (in binary form) about every millisecond in a cyclic buffer. The library provides whatever is in that buffer when the function is called. This low-level function does not capture a whole string, but provides chunks of whatever data was was captured. The provided examples capture the chuncks of data and provide whole strings for further processing.

