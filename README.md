# End-to-end-WSN-Project-2023-2024

## Project Description

This project was developed as part of the course Algorithmic Foundations of Sensor Networks and the Internet of Things in the Computer Enginnering and Informatics Department, University of Patras.

It includes data collection from sensors, storage of this data in a MongoDB database, and real-time visualization through a web application built with Flask.
Finally, we demonstrate the use of several predictive models (e.g., ARIMA) that forecast the next measurement values.

## Question 1: Data Collection

For node communication and data collection from TelosB sensors, the NullNet protocol of Contiki-NG was used.
The data collected (temperature and humidity) are transferred from the leaf sensors to the parent sensor using unicast messages.

## Question 2: Data Storage

For storing the data, a MongoDB database was created.
A named pipe (out_pipe) is used to read data from the parent node, while a Python script saves the data to MongoDB.
The store_data.py script reads data from the pipe and stores it in the database in the correct format.

## Question 3: Data Visualization

For visualization, Flask and Plotly.js were used to create real-time plots.
The application allows users to view live data and retrieve historical data for specific time intervals.
The app.py file contains the Flask server code, while index.html provides the application’s frontend.

## Question 4: Model Training

The collected and stored data in MongoDB were used to train predictive models.
The data were prepared in pandas DataFrames, and models such as ARIMA and LSTM were applied to forecast future temperature and humidity values.
More details can be found in the file model_training.ipynb, and screenshots are included in the report.
## Execution Instructions

1. Install Contiki-NG and Configure the Environment

2. Start Data Collection

On the parent node, run the application to collect data from the sensors and send them to the named pipe.

 #### make TARGET=sky PORT=/dev/ttyUSB0 serialdump > out_pipe

3. Store Data in MongoDB

Run the Python script store_data.py to save the data from the named pipe to MongoDB.

 #### python3 store_data.py

4. Start the Flask Server

Run the Flask application to visualize the data.

 #### python3 app.py

The application will run at: http://127.0.0.1:5000.

5. Train Models and Predict Value
Using the collected data, you can train models to predict future temperature and humidity values.

To train the ARIMA, SARIMAX, LSTM, and SimpleRNN models:

- Open model_training.ipynb in Jupyter Notebook.

- Execute the steps for data preprocessing and model training.

- The model results will include forecasts of future values and accuracy metrics.

To run the Jupyter Notebook:

#### jupyter notebook model_training.ipynb

After running the notebook, the models will be trained with the data, and predictions for temperature and humidity will be generated.

## Further details, analysis, and results are provided in the **report_iot_project.pdf** file (written in greek).
