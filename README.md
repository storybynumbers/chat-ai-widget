## What is this for?
This is a Sendbird Chat AI Widget implemented on top of [React UiKit](https://github.com/sendbird/sendbird-uikit-react).

![chat-ai-widget](https://github.com/sendbird/chat-ai-widget/assets/104121286/360d2a17-dfc6-4810-a7c4-2f0615b43c3d)

## How to use
0. Prepare Sendbird ***Application ID*** and ***Bot ID***
   If you need the Sendbird Application ID and Bot ID, [See How to get Application ID and Bot ID](https://github.com/sendbird/chat-ai-widget/blob/develop/README.md#how-to-get-application-id-and-bot-id)

1. Install Library
   ```bash
   npm install @sendbird/chat-ai-widget
   ```

2. Add `import ...` and `<ChatAiWidget/>` Component to your Code.
   ```jsx
   import { ChatAiWidget } from "@sendbird/chat-ai-widget";
   import "@sendbird/chat-ai-widget/dist/style.css";
   
   const App = () => {
     return (
      <ChatAiWidget
        applicationId="AE8F7EEA-4555-4F86-AD8B-5E0BD86BFE67" // Your Sendbird Application ID
        botId="khan-academy-bot" // Your Bot ID
      />
     );
   }
   ```

  > Not using React in your environment? You can also load this Chat AI Widget component from an HTML file on your website. Please refer to [js-example.html](./js-example.html) for an example.

## Run locally
```bash
npm install
npm run dev
```
 - If you want to change `applicationId` and `botId` when running in local, modify the below two variables in `.env`
   ```
   # Vite prefix is required for Vite to load the env variables
   # Plz modify below two env variables on your needs
   VITE_CHAT_WIDGET_APP_ID=AE8F7EEA-4555-4F86-AD8B-5E0BD86BFE67
   VITE_CHAT_WIDGET_BOT_ID=khan-academy-bot
   ```


## Demo URL
https://sendbird.github.io/chat-ai-widget/


## How to get Application ID and Bot ID
### Prerequisites
- **Sendbird Account:** Go to [Sendbird Dashboard](https://dashboard.sendbird.com/) and create an account for a free trial. If you already have a Sendbird account, sign into your account.
- **Create a Application:**
  1. Create a new application by clicking **Create +** at the bottom right of your screen.
  2. Enter a name for your application. Choose a **Product Type** and **Region**. Then, click **Confirm**.
  3. Click the application you just created under **Applications**. You will see the application's Application ID which you will need when initializing the Chat SDK.
- **Knowledge Base Source:** Prepare data for AI ChatBot to reference in `PDF` or `txt` format and `URL`. This data will serve as the Knowledge Base Source that AI Chatbot will use to generate responses.
  - References for Tutorial

### 1. Navigate to Your Sendbird Application
1. Navigate to the application you created on the Sendbird Dashboard.
2. In the dashboard, navigate to the **Chat** menu and click on **AI Chatbot** under it.
   <img width="1000" alt="image" src="https://github.com/sf-luke-cha/ai-chatbot-tutorial/assets/104121286/e7d00cf0-fcf0-440b-8506-b46c077fff0d">

### 2. Set Up Your AI Chatbot
1. Click on the **Create Bot** button to set up a new AI chatbot.
2. In the **Bot Name** field, enter **Bot Name** you want, and make sure to select a unique **Bot ID**(will be used to invite Bot when creating a new Chat Room).
3. For the **Bot AI Engine**, select **OpenAI ChatGPT** for this time.
4. Specify the **Knowledge Base Source**. There are three options:
   - None: This uses the basic OpenAI Model, and you can adjust the specific parameters to suit your needs.
   
     <img width="300" alt="image" src="https://github.com/sf-luke-cha/ai-chatbot-tutorial/assets/104121286/c6912865-a88c-4e9f-b7cf-99569ffee8ae">

   - File: In this option, you can select a **PDF** or **txt** file as the Knowledge Base Source.
   
     <img width="600" alt="image" src="https://github.com/sf-luke-cha/ai-chatbot-tutorial/assets/104121286/7210bafe-1d42-4593-aae2-180cd6375689">

   - URL: In this option, the contents of a specified **URL** will be automatically analyzed and used as the Knowledge Base Source.
   
     <img width="600" alt="image" src="https://github.com/sf-luke-cha/ai-chatbot-tutorial/assets/104121286/356bd70d-9e47-4638-8687-1cd2f00abe56">

5. Click on the **Create** button to create your AI Chatbot.

### 3. Testing Your AI Chatbot
After your chatbot has been created, you can start testing conversations directly from the web interface.
<img width="800" alt="image" src="https://github.com/sf-luke-cha/ai-chatbot-tutorial/assets/104121286/f1d39df3-b50a-4c6d-a419-ef4bca5dcb87">

## Basic Customization
You can customize the UI of the ChatBot by using the `ChatAiWidget` component. The following are the props that can be used to customize the UI.

```jsx
import { ChatAiWidget } from "@sendbird/chat-ai-widget";
import '@sendbird/chat-ai-widget/dist/style.css';

import { ReactComponent as StartingPageLogo } from './icons/sendbird-logo-starting-page.svg';
import { ReactComponent as StartingPageBackground } from './icons/starting-page-bg-image-svg.svg';


const customConstants = {
  applicationId: 'AE8F7EEA-4555-4F86-AD8B-5E0BD86BFE67', // Your Sendbird application ID
  botId: 'khan-academy-bot', // Your Sendbird bot ID
  botNickName: 'Khan Academy Support Bot',
  userId: 'user1', // Specify your userId. If it's not provided, it'll generate a random one \w uuid
  userNickName: 'User',
  betaMark: true,
  suggestedMessageContent: {
    replyContents: [
      {
        title: 'Yes, it was helpful! 👍',
        text: 'Thanks for your feedback! You can also build your own AI chatbot in Sendbird.',
        buttonText: 'Try free trial',
        link: 'https://dashboard.sendbird.com/auth/signup',
      },
      {
        title: 'No, I need more help. 💬',
        text: "I'm sorry, we couldn't help you. Let us know how we can improve by talking to one of our teammates.",
        buttonText: 'Talk to an expert',
        link: 'https://sendbird.com/contact-sales',
      },
    ],
    messageFilterList: [
      'Can you please clarify?',
      'How can I assist you',
      'How can I help you',
      'Can you clarify',
      "That's not a question I can answer unfortunately",
      'Try again',
      "I couldn't find the answer to your question",
      'Can you try again?',
      'I apologize for any confusion',
      "I'm sorry, I couldn't understand your question",
      "That's not a valid question",
      'Is there a specific question you have',
      "I'm here to help you with any questions you have",
    ],
  },
  firstMessageData: [
    {
      data: [
        {
          suggested_replies: [
            'What can I learn from Pre-K 8th grade?',
            'Tell me about Math',
          ],
        },
      ],
      message: "Hi~ I'm Khan Academy Support ChatBot. Ask me anything!",
    },
  ],
  createGroupChannelParams: {
    name: 'Khan Academy Support Bot',
    coverUrl:
      'https://images.unsplash.com/photo-1526304640581-d334cdbbf45e?ix' +
      'lib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80',
  },
  startingPageContent: {
    headerContent: {
      headerOne: "I'm Khan Academy Support Bot",
      headerTwo: 'Ask me anything!',
    },
    messageContent: {
      header: 'AI ChatBot',
      body: "Hi~ I'm Khan Academy Support ChatBot. Ask me anything!",
    },
    logoContent: {
      Component: StartingPageLogo,
      width: '100px',
    },
    backGroundContent: {
      Component: StartingPageBackground,
      height: '240px',
    },
  },
  chatBottomContent: {
    text: 'Sendbird AI ChatBot',
    backgroundColor:
      'linear-gradient(273.73deg, #4DCD90 -0.83%, #6210CC 48.04%, #6210CC 75.45%)',
  },
  messageBottomContent: {
    text: 'AI-generated response powered by OpenAI',
    infoIconText:
      'In this beta version, the AI-generated responses may lack complete accuracy.',
  },
  replacementTextList: [['the Text extracts', 'ChatBot Knowledge Base']],
  enableSourceMessage: false,
  enableEmojiFeedback: true,
  enableMention: true,
  autoOpen: false,
  // Added for branding customization:
  branding: {
      // String for CSS background for widget
      chatButtonBackground: "#ffcc00";
      // Component ro render inside the widget, to replace the default icon
      chatBotIcon: MyCustomIcon;
      // Set to false to hide Sendbird branding
      showSendbirdAttribution: false;
  }
};

const App = () => {
  return (
    <ChatAiWidget
      applicationId={customConstants.applicationId}
      botId={customConstants.botId}
      botNickName={customConstants.botNickName}
      userId={customConstants.userId}
      userNickName={customConstants.userNickName}
      betaMark={customConstants.betaMark}
      customBetaMarkText={customConstants.customBetaMarkText}
      suggestedMessageContent={customConstants.suggestedMessageContent}
      firstMessageData={customConstants.firstMessageData}
      createGroupChannelParams={customConstants.createGroupChannelParams}
      startingPageContent={customConstants.startingPageContent}
      chatBottomContent={customConstants.chatBottomContent}
      messageBottomContent={customConstants.messageBottomContent}
      replacementTextList={customConstants.replacementTextList}
      enableSourceMessage={customConstants.enableSourceMessage}
      enableEmojiFeedback={customConstants.enableEmojiFeedback}
      enableMention={customConstants.enableMention}
      branding={customConstants.branding}
    />
  );
};

export default App;

```

## Advanced Customization
```jsx
import { ChatAiWidget } from "@sendbird/chat-ai-widget";
import '@sendbird/chat-ai-widget/dist/style.css';

import { SessionHandler } from '@sendbird/chat'

// Replace below with the real one
const USER_ID = 'UserId';

/**
 * To setup auth on their own API,
 * You can also create your own custom session handler \w userId.
 * More information can be found in
 * https://sendbird.com/docs/chat/v3/javascript/guides/authentication
 * Also, we recommend to memoize this configureSession function,
 * before you pass to ChatAiWidget component.
 * */
const issueSessionToken = async (userId, ...) => {
  // build your own API request handler
};

const memoizedConfigureSession = useCallback(
  (sdk) => {
    const sessionHandler = new SessionHandler();
    sessionHandler.onSessionTokenRequired = (resolve, reject) => {
      console.warn('SessionHandler.onSessionTokenRequired()');
      // This issueSessionToken fn i
      issueSessionToken(USER_ID)
        .then(token => {
          // curentUserInfo.accessToken = token;
          resolve(token);
        })
        .catch(err => reject(err));
    };
    sessionHandler.onSessionRefreshed = () => {
      console.warn('SessionHandler.onSessionRefreshed()');
    };
    sessionHandler.onSessionError = (err) => {
      console.warn('SessionHandler.onSessionError()', err);
    };
    sessionHandler.onSessionClosed = () => {
      console.warn('SessionHandler.onSessionClosed()');
    };
    console.warn(sessionHandler);
    return sessionHandler;
  },[]);

const customConfigs = {
  // If instantConnect set to `true`, the SDK connection will be established right after mounting the Chat or ChatAiWidget component
  instantConnect: true / false,
  // `autoOpen` determines whether the chatbot widget automatically opens
  // when the user opens the browser window.
  // The default behavior is to open after a certain period,
  // but setting this option to `true` will keep it open at all times.
  autoOpen: true / false,
  configureSession: memoizedConfigureSession,
  customRefreshComponent: {
    icon: 'Your SVG icon',
    style: {
      position: 'relative' as React.CSSProperties['position'],
      right: 0,
    },
    width: '16px',
    height: '16px',
    onClick: () => { ... },
  }
}

const customConstants = {
  // Add other constant props like in the basic customization section above
}

const App = () => {
  return (
    <ChatAiWidget
      userId={USER_ID}
      configureSession={customConfigs.configureSession}
      customRefreshComponent={customConfigs.customRefreshComponent}
      instantConnect={customConfigs.instantConnect}
      autoOpen={customConfigs.autoOpen}
      {...customConstants}
    />
  );
};

export default App;
```
