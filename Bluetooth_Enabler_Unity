using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TechTweaking.Bluetooth;
using UnityEngine.UI;

public class BluetoothListener:MonoBehaviour
{
    private BluetoothDevice device;
    public Text statusText;

    private void Awake()
    {
        BluetoothAdapter.enableBluetooth();
        device = new BluetoothDevice();
        device.Name = "HC-05";
        //device.MacAddress = "98.D3.31.FB.20.EE";
    }
    public void Update()
    {
        if(device.IsConnected && device.IsReading)
        {
            byte[] message = device.read();
            if(message != null)
            {
                string content = System.Text.Encoding.ASCII.GetString(message);
                statusText.text = content;
            }
        }
    }

    public void Connect()
    {
        statusText.text = "Status...";
        device.connect();
        if(device.IsConnected)
        {
            statusText.text = "Connection Success with " + device.Name;

        }
        else
        {
            statusText.text = "Connection Failed";

        }
    }

    public void Disconnect()
    {
        device.close();
        statusText.text = "Status: Disconnecting Bluetooth";
    }

    public void Send()
    {
        device.send(System.Text.Encoding.ASCII.GetBytes("Hello\n"));
        statusText.text = "Status: Sending Hello";
    }

    public bool Ishotting()
    {
        if (device.IsConnected && device.IsReading)
        {
            byte[] message = device.read();
            if (message != null)
            {
                string content = System.Text.Encoding.ASCII.GetString(message);
                if (content == "1")
                {
                    return true;
                }

            }

        }
        return false;
    }
}


