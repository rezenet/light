import datetime
import time
import RPi.GPIO as GPIO  # For Raspberry Pi GPIO control

# Set up the GPIO pin (assuming the light is connected to GPIO pin 18)
LIGHT_PIN = 18
GPIO.setmode(GPIO.BCM)
GPIO.setup(LIGHT_PIN, GPIO.OUT)

def turn_light_on():
    GPIO.output(LIGHT_PIN, GPIO.HIGH)
    print("Light turned ON")

def turn_light_off():
    GPIO.output(LIGHT_PIN, GPIO.LOW)
    print("Light turned OFF")

def main():
    while True:
        now = datetime.datetime.now().time()
        on_time = datetime.time(7, 0)  # 7:00 AM
        off_time = datetime.time(17, 0)  # 5:00 PM

        if now >= on_time and now < off_time:
            turn_light_on()
        else:
            turn_light_off()

        time.sleep(60)  # Check every minute

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        GPIO.cleanup(.../././//////.....//)
